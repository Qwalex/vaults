
Поиск проектов в группе
Поиск вхождений в проекте
fetch(`https://gitlab.services.mts.ru/api/v4/projects/${window.projectIds[0]}/search?scope=blobs&search=header&per_page=200`).then(a => a.json()).then((d) => console.log(d))

> реализовать в response.length < infinity = per_page = infitity

```ts
const FINTECH_GROUP_ID = 856

const getAllGroups = async () => await fetch(`https://gitlab.services.mts.ru/api/v4/groups/${FINTECH_GROUP_ID}/descendant_groups?per_page=200`).then(a => a.json())
```

```ts
const getGroupProjects = async (groupId) => await fetch(`https://gitlab.services.mts.ru/api/v4/groups/${groupId}/projects?per_page=200`).then(a => a.json())
```

```ts
window.projects = []
allGroupsIds.map(p => p.id).forEach(id => getGroupProjects(id).then(data => window.projects.concat(data)))
```


```ts


window.qresponseResult = []
const delay = (ms) => new Promise(resolve => setTimeout(resolve, ms));

const searchByIds = async (string, ids) => {
    for (const id of ids) {
        await delay(1000); // Задержка между запросами
        try {
            const response = await fetch(`https://gitlab.services.mts.ru/api/v4/projects/${id}/search?scope=blobs&search=${string}&per_page=100`);
            const result = await response.json();
            if (Array.isArray(result) && result.length > 0) {
                const { name, ...project } = window.projects.find(p => p.id === id);
								console.log({
                    id,
                    project,
                    name,
                    result,
                })
                window.qresponseResult.push({
                    id,
                    project,
                    name,
                    result,
                });
            }
        } catch (error) {
            console.error(`Ошибка при поиске по ID ${id}:`, error);
        }
    }
		console.log('Поиск завершен');
}

const FINTECH_GROUP_ID = 856;
window.projects = [];

const getAllGroups = async () => {
    const response = await fetch(`https://gitlab.services.mts.ru/api/v4/groups/${FINTECH_GROUP_ID}/descendant_groups?per_page=200`);
    return await response.json();
}

const getGroupProjects = async (groupId) => {
    const response = await fetch(`https://gitlab.services.mts.ru/api/v4/groups/${groupId}/projects?per_page=200`);
    return await response.json();
}

window.allGroups = await getAllGroups();
for (const { id } of window.allGroups) {
    const projects = await getGroupProjects(id);
    window.projects.push(...projects); // Используем push для добавления проектов
}

window.projectsId = window.projects.map(({ id }) => id);
window.allGroupIds = window.allGroups.map(item => item.id);
```

FooterMenu
FooterMain

{id: 161243, project: {…}, name: 'Portal Mtsdengi Main Page', result: Array(1)}
{id: 169367, project: {…}, name: 'Portal Mtsdengi Frontend Offices', result: Array(1)}
{id: 168446, project: {…}, name: 'Frontend Unauth App Config', result: Array(5)}
{id: 177591, project: {…}, name: 'Portal Mtsdengi Frontend Credit Cards Page', result: Array(1)}
{id: 176807, project: {…}, name: 'Portal Mtsdengi Frontend Cash Loan', result: Array(1)}
{id: 169663, project: {…}, name: 'Portal Mtsdengi Universal Forms Page', result: Array(1)}
{id: 180638, project: {…}, name: 'Portal Mtsdengi Frontend Deposits', result: Array(1)}

UMP_BACKEND_HOST
{id: 162093, project: {…}, name: 'mtsdengi-ansible', result: Array(8)}
{id: 165277, project: {…}, name: 'mtsdengi-common', result: Array(1)}
{id: 168446, project: {…}, name: 'Frontend Unauth App Config', result: Array(4)}
{id: 161868, project: {…}, name: 'Frontend MF App Config', result: Array(4)}


если по поиску в группе fintech

дадата -  по вхождению /s/suggest 
```js
[
    "portal-frontend-ipoteka",
    "web-dbo-payments",
    "portal-frontend-small-business",
    "portal-frontend-msb-package",
    "React Модуль анкет",
    "React Микросервис карт",
    "React Модуль анкет_broken",
    "front-education-pos",
    "pos-package",
    "Portal frontend premium",
    "site2-static01",
    "Portal Frontend Small Business",
    "Portal Frontend Corporate Business",
    "Frontend App Config",
    "Frontend Maps",
    "Common",
    "Portal Frontend Landings Landing Factory",
    "Portal Frontend Landing Factory V2",
    "Portal Frontend Double Offer",
    "Portal Frontend Deposit Package",
    "Portal Frontend Delivery Statuses",
    "Portal Frontend Corporative Clients",
    "Portal Frontend Corporate Business",
    "Portal Frontend Small Business",
    "portal-frontend-loans-package",
    "portal-frontend-loans",
    "frontend-calc-main-fe",
    "Portal Mtsdengi Frontend Full Approve Form",
    "Portal Mtsdengi Frontend Credit Cards Page",
    "Portal Mtsdengi Frontend Cash Loan",
    "Portal Mtsdengi Universal Forms Page",
    "Portal Mtsdengi Frontend Maps",
    "Frontend Unauth App Config",
    "Portal Mtsdengi Frontend Pip C2C",
    "Portal Mtsdengi Universal Forms",
    "Portal Mtsdengi Frontend Pip",
    "Frontend MF App Config",
    "ui-kit"
]
```

recaptha - по вхождению `<GoogleReCaptchaProvider`

```js
 [
    "portal-frontend-small-business-landing",
    "portal-frontend-small-business",
    "portal-frontend-msb-package",
    "Portal Frontend Private Banking",
    "Portal frontend premium",
    "portal-frontend-support-feedback",
    "Portal Frontend Small Business",
    "Portal Frontend Corporate Business",
    "Portal Frontend Private Banking",
    "Portal Frontend Landing Factory V2",
    "Portal Frontend Invest Uslugi",
    "Portal Frontend Eng",
    "Portal Frontend Deposit Package",
    "Portal Frontend Corporative Clients",
    "Portal Frontend About Bank",
    "Portal Frontend About Bank Test Ci",
    "Portal Frontend Corporate Business",
    "Portal Frontend Small Business"
]
```