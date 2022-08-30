| **Reporter**        | **Github Pages**   | **Azure Storage Static Website** | **AWS S3 Static Website**                                                                    |
|---------------------|--------------------|-------------------------------|----------------------------------------------------------------------------------------------|
| **Allure HTML**     | [GH Action Link](https://github.com/marketplace/actions/allure-html-reporter-github-pages) | [GH Action Link](https://github.com/marketplace/actions/allure-html-reporter-azure-website)            | [GH Action Link](https://github.com/marketplace/actions/allure-html-reporter-aws-s3-website )      |
| **Any HTML Reports** | [GH Action Link](https://github.com/marketplace/actions/html-reporter-github-pages) | [GH Action Link](https://github.com/marketplace/actions/html-reporter-azure-website)            | [GH Action Link](https://github.com/marketplace/actions/html-reporter-aws-s3-website) |



## Use Cases:- Publish HTML Test Results on GitHub Pages with History Tracking. Few examples listed below.

- Code Coverage HTML Reports in JaCoCo or Cobertura format
  - JUnit5(JaCoCo)
  - NUNIT/MSTest(Cobertura)
  - JEST(Cobertura)
  - Jasmine/Karma(Cobertura)
  - Pytest(Cobertura)
  
- HTML Test Results from Selenium4, WebDriverIO, Playwright in below formats.
  - Allure HTML Reporter (any programming language)
  - Cucumber HTML Reporter (any programming language)
  - Playwright HTML Reporter (TypeScript)
  - Extent HTML Reporter (CSharp, Java)
  - SpecFlow Living Documents (CSharp)
  
- Performance Test Results from JMeter, K6.io and Locust.io

## Inputs

This Action defines the following formal inputs.

| Name | Required | Default | Description
|-|-|-|-|
| **`workflow_id`**  | true | none | Provide name of your workflow file. Example ci.yml
| **`test_results`** | true | none | provide name of the folder that has got the index.html and other static files to deploy on GH Pages. Example if my folder that has got all my test results is html-report then i would enter "html-report" as input value.
| **`subfolder`** | false | none | Provide the subfolder in case if your files that have index.html and other static content in present in subfolder. say i have a folder called "archive" and under that i have subfolder "html-report" in that case i would enter 'archive' for variable 'test_results' and 'html-report' under 'subfolder'
| **`gh_pages`** | false | gh_pages | name of the branch where you would like to push your static content to be published. Ideally it should be called gh_pages so default it to same but you have choice to modify it.
| **`keep_reports`** | false | 20 |  Number of reports you would like to retain. There is a 5GB limit on Git Repo. Defaulted to 20 reports but if you but ideally you should do math to calculate how many reports you could store. if your report size is say 50 MB then you could store up to a 100 reports.
|**`github_repo`** | false | ${{ github.repository }} | repo name that you would like to push gh-pages branch to. we default it to your curent repo where workflow is being run. If you would like to push to another repo please enter in format "tr/project-awesome" in this format.
|**`report_url`** | false | None | Enter the URL of your GitHub Pages Site. It could be the generated by GitHub Pages or it could be Route 53 URL with Cloudfront ending with thomsonreuters.com 

## Outputs

This Action defines the following formal outputs.

None

## Example workflow - same repo

      - name: GH Pages Push
        uses: tr/cicd_gh-actions-gh-pages@v1.0
        with:
          test_results: test-results
          keep_reports: 20
          workflow_id: main.yml


## Example workflow - different repo

      - name: GH Pages Push
        uses: PavanMudigonda/html-reporter-github-pages@v1.0
        with:
          test_results: test-results
          keep_reports: 20
          workflow_id: main.yml
          token: ${{ secrets.PAT }}
          github_repo: PavanMudigonda/another-awesome-repo

### Sample GH Pages Home Page

<img width="626" alt="image" src="https://user-images.githubusercontent.com/29324338/174328988-d53bc4bd-e189-4179-8a42-2046b8c83a9b.png">

### Sample GH Pages Test Results

<img width="1287" alt="image" src="https://user-images.githubusercontent.com/29324338/174329137-a76d7c84-62b0-4724-aa37-440ea753b740.png">


