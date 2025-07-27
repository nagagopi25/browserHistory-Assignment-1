#index.css
.history-item-container {
  list-style-type: none;
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
  width: 100%;
}
.time-accessed {
  margin-bottom: 10px;
  color: #64748b;
  font-size: 15px;
  font-weight: bold;
}
.history-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 100%;
}
.history-content {
  width: 100%;
  display: flex;
  flex-direction: row;
}
.domain-logo {
  height: 28px;
  width: 28px;
  margin-right: 14px;
}
.title-domain-container {
  display: flex;
  flex-direction: column;
}
.title {
  margin: 0px;
  color: #475569;
  font-weight: bold;
}
.domain {
  margin: 0px;
  color: #64748b;
  font-weight: 400;
}
.button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  outline: none;
}

@media screen and (min-width: 768px) {
  .history-item-container {
    flex-direction: row;
    align-items: center;
  }
  .time-accessed {
    width: 100px;
  }
  .title {
    margin-right: 10px;
  }
  .title-domain-container {
    flex-direction: row;
  }
}


#BrowserHistory-> index.js
import './App.css'
import {Component} from 'react'
import BrowserHistoryItem from './BrowserHistoryItem'

const initialHistoryList = [
  {
    id: 0,
    timeAccessed: '07:45 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/instagram-img.png',
    title: 'Instagram',
    domainUrl: 'instagram.com',
  },
  {
    id: 1,
    timeAccessed: '05:45 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/twitter-img.png',
    title: 'Twitter. It’s what’s happening / Twitter',
    domainUrl: 'twitter.com',
  },
  {
    id: 2,
    timeAccessed: '04:35 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/facebook-img.png',
    title: 'Facebook – log in or sign up',
    domainUrl: 'facebook.com',
  },
  {
    id: 3,
    timeAccessed: '04:25 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/linkedin-img.png',
    title: 'LinkedIn: Log In or Sign Up',
    domainUrl: 'linkedin.com',
  },
  {
    id: 4,
    timeAccessed: '04:00 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/hashnode-img.png',
    title: 'Hashnode: Everything you need to start blogging as a developer!',
    domainUrl: 'hashnode.com',
  },
  {
    id: 5,
    timeAccessed: '03:25 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/github-img.png',
    title: 'GitHub: Where the world builds software · GitHub',
    domainUrl: 'github.com',
  },
  {
    id: 6,
    timeAccessed: '02:45 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/react-img.png',
    title: 'React – A JavaScript library for building user interfaces',
    domainUrl: 'reactjs.org',
  },
  {
    id: 7,
    timeAccessed: '01:25 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/stackoverflow-img.png',
    title: 'Stack Overflow - Where Developers Learn, Share, & Build Careers',
    domainUrl: 'stackoverflow.com',
  },
  {
    id: 8,
    timeAccessed: '09:25 AM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/gmail-img.png',
    title: 'Gmail',
    domainUrl: 'mail.google.com',
  },
  {
    id: 9,
    timeAccessed: '09:00 AM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/google-img.png',
    title: 'Google',
    domainUrl: 'google.com',
  },
]

class App extends Component {
  state = {
    userInput: '',
    historyList: initialHistoryList,
  }

  onChangeInput = event => {
    this.setState({userInput: event.target.value})
  }

  deleteHistory = id => {
    const {historyList} = this.state
    const updatedList = historyList.filter(each => each.id !== id)
    this.setState({historyList: updatedList})
  }

  render() {
    const {userInput, historyList} = this.state
    const searchResults = historyList.filter(each =>
      each.title.toLowerCase().includes(userInput.toLowerCase()),
    )

    console.log('Search input:', userInput)
    console.log('Filtered search results:', searchResults)
    console.log('Current history list:', historyList)
    return (
      <div className="app-container">
        <div className="app-header">
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
              placeholder="Search history"
              className="search-input"
              onChange={this.onChangeInput}
              value={userInput}
            />
          </div>
        </div>

        <div className="app-footer">
          {searchResults.length === 0 ? (
            <p>There is no history to show</p>
          ) : (
            <ul className="history-list">
              {searchResults.map(eachHistory => (
                <BrowserHistoryItem
                  key={eachHistory.id}
                  history={eachHistory}
                  deleteHistory={this.deleteHistory}
                />
              ))}
            </ul>
          )}
        </div>
      </div>
    )
  }
}

export default App
#APP.css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.app-container {
  background-color: #ffffff;
  min-height: 100vh;
}
.app-header {
  background-color: #3367d6;
  padding: 20px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.app-logo {
  height: 20px;
  margin-right: 20px;
}

.search-container {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.search-bar-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 100%;
}

@media screen and (min-width: 768px) {
  .search-bar-container {
    width: 60%;
  }
}

.logo-container {
  background-color: #2850a7;
  height: 40px;
  width: 40px;
  padding: 5px 8px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin-right: 3px;
}
.search-input {
  height: 40px;
  width: 100%;
  background-color: #2850a7;
  outline: none;
  border: none;
  padding: 5px 16px;
  color: #ffffff;
}

.app-footer {
  background-color: #ececec;
  padding: 30px;
  min-height: 100vh;
}
.history-list-container {
  background-color: #ffffff;
  box-shadow: 0px 4px 16px 0px #bfbfbf;
  padding: 20px;
  width: 100%;
}
.no-history-con {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.no-history {
  font-size: 18px;
  color: #475569;
  font-weight: 500;
}

#APP.js

import './App.css'
import {Component} from 'react'
import BrowserHistoryItem from './BrowserHistoryItem'

const initialHistoryList = [
  {
    id: 0,
    timeAccessed: '07:45 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/instagram-img.png',
    title: 'Instagram',
    domainUrl: 'instagram.com',
  },
  {
    id: 1,
    timeAccessed: '05:45 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/twitter-img.png',
    title: 'Twitter. It’s what’s happening / Twitter',
    domainUrl: 'twitter.com',
  },
  {
    id: 2,
    timeAccessed: '04:35 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/facebook-img.png',
    title: 'Facebook – log in or sign up',
    domainUrl: 'facebook.com',
  },
  {
    id: 3,
    timeAccessed: '04:25 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/linkedin-img.png',
    title: 'LinkedIn: Log In or Sign Up',
    domainUrl: 'linkedin.com',
  },
  {
    id: 4,
    timeAccessed: '04:00 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/hashnode-img.png',
    title: 'Hashnode: Everything you need to start blogging as a developer!',
    domainUrl: 'hashnode.com',
  },
  {
    id: 5,
    timeAccessed: '03:25 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/github-img.png',
    title: 'GitHub: Where the world builds software · GitHub',
    domainUrl: 'github.com',
  },
  {
    id: 6,
    timeAccessed: '02:45 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/react-img.png',
    title: 'React – A JavaScript library for building user interfaces',
    domainUrl: 'reactjs.org',
  },
  {
    id: 7,
    timeAccessed: '01:25 PM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/stackoverflow-img.png',
    title: 'Stack Overflow - Where Developers Learn, Share, & Build Careers',
    domainUrl: 'stackoverflow.com',
  },
  {
    id: 8,
    timeAccessed: '09:25 AM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/gmail-img.png',
    title: 'Gmail',
    domainUrl: 'mail.google.com',
  },
  {
    id: 9,
    timeAccessed: '09:00 AM',
    logoUrl: 'https://assets.ccbp.in/frontend/react-js/google-img.png',
    title: 'Google',
    domainUrl: 'google.com',
  },
]

class App extends Component {
  state = {
    userInput: '',
    historyList: initialHistoryList,
  }

  onChangeInput = event => {
    this.setState({userInput: event.target.value})
  }

  deleteHistory = id => {
    const {historyList} = this.state
    const updatedList = historyList.filter(each => each.id !== id)
    this.setState({historyList: updatedList})
  }

  render() {
    const {userInput, historyList} = this.state
    const searchResults = historyList.filter(each =>
      each.title.toLowerCase().includes(userInput.toLowerCase()),
    )

    console.log('Search input:', userInput)
    console.log('Filtered search results:', searchResults)
    console.log('Current history list:', historyList)

    return (
      <div className="app-container">
        <div className="app-header">
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
              placeholder="Search history"
              className="search-input"
              onChange={this.onChangeInput}
              value={userInput}
            />
          </div>
        </div>

        <div className="app-footer">
          {searchResults.length === 0 ? (
            <p>There is no history to show</p>
          ) : (
            <ul className="history-list">
              {searchResults.map(eachHistory => (
                <BrowserHistoryItem
                  key={eachHistory.id}
                  history={eachHistory}
                  deleteHistory={this.deleteHistory}
                />
              ))}
            </ul>
          )}
        </div>
      </div>
    )
  }
}

export default App

#index.js
// index.js
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import './index.css' // optional, if you have styles

const root = ReactDOM.createRoot(document.getElementById('root'))
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)


#SetupTEST.js
/* eslint-disable */

import '@testing-library/jest-dom'
import {configure} from '@testing-library/react'

configure({testIdAttribute: 'data-testid'})
