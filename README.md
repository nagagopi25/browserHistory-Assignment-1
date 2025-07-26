// src/index.js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'
import './index.css'

ReactDOM.render(<App />, document.getElementById('root'))

// src/App.js
import BrowserHistory from './components/BrowserHistory'

const App = () => <BrowserHistory />

export default App

// src/components/BrowserHistory/index.js
import {useState} from 'react'
import HistoryItem from '../HistoryItem'
import './index.css'

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
    <div className="app-container">
      <nav className="navbar">
        <img
          src="https://assets.ccbp.in/frontend/react-js/history-website-logo-img.png"
          alt="app logo"
          className="app-logo"
        />
        <div className="search-container">
          <img
            src="https://assets.ccbp.in/frontend/react-js/search-img.png"
            alt="search"
            className="search-icon"
          />
          <input
            type="search"
            value={searchInput}
            onChange={onChangeSearch}
            placeholder="Search history"
            className="search-input"
          />
        </div>
      </nav>

      {filteredList.length > 0 ? (
        <ul className="history-list">
          {filteredList.map(each => (
            <HistoryItem key={each.id} item={each} onDelete={onDelete} />
          ))}
        </ul>
      ) : (
        <p className="no-history">There is no history to show</p>
      )}
    </div>
  )
}

export default BrowserHistory

// src/components/HistoryItem/index.js
import './index.css'

const HistoryItem = props => {
  const {item, onDelete} = props
  const {id, timeAccessed, logoUrl, title, domainUrl} = item

  const deleteItem = () => {
    onDelete(id)
  }

  return (
    <li className="history-item">
      <p className="time">{timeAccessed}</p>
      <div className="logo-title">
        <img src={logoUrl} alt="domain logo" className="logo" />
        <div className="text-container">
          <p className="title">{title}</p>
          <p className="domain">{domainUrl}</p>
        </div>
      </div>
      <button
        className="delete-btn"
        onClick={deleteItem}
        data-testid="delete"
      >
        <img
          src="https://assets.ccbp.in/frontend/react-js/delete-img.png"
          alt="delete"
        />
      </button>
    </li>
  )
}

export default HistoryItem

// src/index.css
body {
  font-family: Roboto, sans-serif;
  margin: 0;
  background-color: #f8fafc;
}

.app-container {
  padding: 16px;
}

.navbar {
  background-color: #3367d6;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 16px;
}

.app-logo {
  height: 30px;
}

.search-container {
  background-color: #2850a7;
  display: flex;
  align-items: center;
  padding: 4px;
  border-radius: 4px;
}

.search-icon {
  height: 16px;
  margin-right: 4px;
}

.search-input {
  border: none;
  padding: 4px;
  background-color: transparent;
  color: white;
  outline: none;
}

.history-list {
  list-style: none;
  padding: 0;
  margin-top: 16px;
}

.history-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #ececec;
  padding: 8px 0;
}

.time {
  color: #64748b;
  width: 80px;
}

.logo-title {
  display: flex;
  align-items: center;
  flex: 1;
}

.logo {
  height: 24px;
  margin-right: 8px;
}

.text-container .title {
  margin: 0;
  color: #475569;
  font-weight: bold;
}

.text-container .domain {
  margin: 0;
  color: #64748b;
}

.delete-btn {
  background: none;
  border: none;
  cursor: pointer;
}

.no-history {
  color: #475569;
  text-align: center;
  margin-top: 20px;
}
