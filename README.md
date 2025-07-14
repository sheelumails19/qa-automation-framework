# QA Automation Framework

## 🚀 Features
- ✅ Cross-browser testing (Chrome, Firefox, Safari)
- ✅ Mobile testing (iOS, Android)
- ✅ API testing integration
- ✅ AI-ML powered test generation
- ✅ Parallel execution
- ✅ Docker containerization
- ✅ CI/CD pipeline integration
- ✅ Rich HTML reports
- ✅ Screenshot/video capture
- ✅ Self-healing locators

## 📊 Test Coverage
- UI Tests: 150+ scenarios
- API Tests: 50+ endpoints
- Mobile Tests: 25+ device configurations
- Performance Tests: Load testing integration


# .github/workflows/ci-cd.yml
name: QA Automation Tests

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
    - name: Install dependencies
      run: npm ci
    - name: Install Playwright browsers
      run: npx playwright install --with-deps
    - name: Run tests
      run: npm test
    - name: Upload test results
      uses: actions/upload-artifact@v3
      if: always()
      with:
        name: test-results
        path: test-results/


        
