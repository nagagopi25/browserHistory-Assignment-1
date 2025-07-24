# browserHistory-Assignment-1
src/index.js
jsx

import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'
import './index.css'

ReactDOM.render(<App />, document.getElementById('root'))
#src/App.js
jsx

import BrowserHistory from './components/BrowserHistory'

const App = () => <BrowserHistory />

export default App
# src/components/BrowserHistory/index.js
jsx

import {useState} from 'react'
import HistoryItem from '../HistoryItem'

const initialHistoryList = [
{
id: 0,
timeAccessed: '07:45 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/instagram-img.png',
title: 'Instagram',
domainUrl: 'https://www.instagram.com',
},
{
id: 1,
timeAccessed: '06:30 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/facebook-img.png',
title: 'Facebook',
domainUrl: 'https://www.facebook.com',
},
{
id: 2,
timeAccessed: '05:00 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/twitter-img.png',
title: 'Twitter',
domainUrl: 'https://www.twitter.com',
},
{
id: 3,
timeAccessed: '04:30 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/linkedin-img.png',
title: 'LinkedIn',
domainUrl: 'https://www.linkedin.com',
},
{
id: 4,
timeAccessed: '03:15 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/youtube-img.png',
title: 'YouTube',
domainUrl: 'https://www.youtube.com',
},
{
id: 5,
timeAccessed: '02:45 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/google-img.png',
title: 'Google',
domainUrl: 'https://www.google.com',
},
{
id: 6,
timeAccessed: '01:00 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/github-img.png',
title: 'GitHub',
domainUrl: 'https://www.github.com',
},
{
id: 7,
timeAccessed: '12:15 PM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/stackoverflow-img.png',
title: 'Stack Overflow',
domainUrl: 'https://stackoverflow.com',
},
{
id: 8,
timeAccessed: '11:00 AM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/netflix-img.png',
title: 'Netflix',
domainUrl: 'https://www.netflix.com',
},
{
id: 9,
timeAccessed: '10:30 AM',
logoUrl: 'https://assets.ccbp.in/frontend/react-js/amazon-img.png',
title: 'Amazon',
domainUrl: 'https://www.amazon.com',
},
]

const BrowserHistory = () => {
const [searchInput, setSearchInput] = useState('')
const [historyList, setHistoryList] = useState(initialHistoryList)

const onChangeSearch = event => {
setSearchInput(event.target.value)
}

const onDelete = id => {
const updatedList = historyList.filter(each => each.id !== id)
setHistoryList(updatedList)
}

const filteredList = historyList.filter(each =>
each.title.toLowerCase().includes(searchInput.toLowerCase())
)

return (
<div>
<nav>
<img
src="https://assets.ccbp.in/frontend/react-js/history-website-logo-img.png"
alt="app logo"
/>
<div>
<img
src="https://assets.ccbp.in/frontend/react-js/search-img.png"
alt="search"
/>
<input
type="search"
value={searchInput}
onChange={onChangeSearch}
placeholder="Search history"
/>
</div>
</nav>

{filteredList.length > 0 ? (
<ul>
{filteredList.map(each => (
<HistoryItem key={each.id} item={each} onDelete={onDelete} />
))}
</ul>
) : (
<p>There is no history to show</p>
)}
</div>
)
}

export default BrowserHistory
# src/components/HistoryItem/index.js
jsx

const HistoryItem = props => {
const {item, onDelete} = props
const {id, timeAccessed, logoUrl, title, domainUrl} = item

const deleteItem = () => {
onDelete(id)
}

return (
<li>
<p>{timeAccessed}</p>
<img src={logoUrl} alt="domain logo" />
<p>{title}</p>
<p>{domainUrl}</p>
<button data-testid="delete" onClick={deleteItem}>
<img
src="https://assets.ccbp.in/frontend/react-js/delete-img.png"
alt="delete"
/>
</button>
</li>
)
}

export default HistoryItem
# src/index.css (Optional Styling)
css

body {
font-family: Arial, sans-serif;
margin: 0;
padding: 0;
}

nav {
display: flex;
justify-content: space-between;
align-items: center;
padding: 10px;
background-color: #ededed;
}

input[type="search"] {
padding: 6px;
font-size: 14px;
}

ul {
list-style: none;
padding: 0;
}

li {
display: flex;
align-items: center;
justify-content: space-between;
padding: 10px;
border-bottom: 1px solid #ccc;
}
