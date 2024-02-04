# azure-built-in-auth
Built In Authentication for Azure Static Web App Using Entra ID

Azure Static Web Apps provide built-in authentication by defining routing rules in the configuration file

staticwebapp.config.json

GETTING STARTED
1. Create a repo on github azure-built-in-auth
2. Create a folder on local azure-built-in-auth
3. CD into azure-built-in-auth
4. git init
5. git add README.md
6. git commit -m "Initial commit"
7. git branch -M main
8. git remote add origin https://github.com/{YOUR-ACCOUNT-NAME}/azure-built-in-auth.git
9. git push -u origin main
10. Done

CREATE CONFIG

1. CD into azure-built-in-auth
2. echo '{
  "routes": [
    {
      "route": "/anonymous/*",
      "allowedRoles": ["anonymous"]
    },
    {
      "route": "/authenticated/*",
      "allowedRoles": ["authenticated"]
    },
    {
      "route": "/custom/*",
      "allowedRoles": ["custom"]
    }
  ]
}' > staticwebapp.config.json

CREATE 3 FOLDERS FOR ROLES
1. mkdir anonymous
2. mkdir authenticated
3. mkdir custom
4. mkdir anonymous authenticated custom (this will also work for 1,2,3)
5. mkdir -p anonymous authenticated custom
6. echo '<html lang="en">
<body>
    <h1>Azure Static Web Apps auth demo</h1>
    <div>
        <a href="/.auth/login/aad">Login</a>
        <a href="/.auth/logout">Logout</a>
    </div>
    <div>
        <ul>
            <li><a href="/anonymous/">Anonymous Role page</a></li>
            <li><a href="/authenticated/">Authenticated Role page</a></li>
            <li><a href="/custom/">Custom Role page</a></li>
        </ul>
    </div>
</body>
</html>' | tee anonymous/index.html authenticated/index.html custom/index.html > /dev/null

DESCRIPTION

Each user belongs to the built-in anonymous role, all logged in user are members of authenticated role.
Even if a user does not login, the use is default to having anonymous role.
After user logs in user is default to having authenticated role
We also define a custom role to associate uses via invitations.

CREATE INVITATION LINKE