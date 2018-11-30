stage("Sanity Check") {
  node {
    ws('workspace/d2l-en') {
      checkout scm
      sh "build/sanity_check.sh"
    }
  }
}


stage("Build HTML") {
  node {
    ws('workspace/d2l-en') {
      checkout scm
      sh "build/build_html.sh"
    }
  }
}

stage("Build PDF") {
  node {
    ws('workspace/d2l-en') {
      checkout scm
      sh "build/build_pdf.sh"
    }
  }
}

stage("Build PKG") {
  node {
    ws('workspace/d2l-en') {
	  checkout scm
      sh "build/build_pkg.sh"
    }
  }
}

stage("Publish") {
  node {
    ws('workspace/d2l-en') {
      sh """#!/bin/bash
      set -ex
      if [[ ${env.BRANCH_NAME} == master ]]; then
          build/upload.sh
      fi
      """
    }
  }
}
