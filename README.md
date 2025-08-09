# Codemagic-
git add codemagic.yaml git commit -m "Add Codemagic workflow" git push
workflows:
  default-workflow:
    name: Default Workflow
    environment:
      flutter: 3.32.6 # Specify Flutter version explicitly
      xcode: latest
    triggering:
      events:
        - push
      branch_patterns:
        - pattern: master
          include: true
          source: true
    scripts:
      - name: Clone repository
        script: |
          git clone https://github.com/mustafa9485/BRUTEFORCEnew.git .
      - name: List files for debugging
        script: |
          ls -R .
      - name: Clean Flutter project
        script: |
          flutter clean
      - name: Get Flutter packages
        script: |
          flutter pub get
      - name: Build Flutter (Web)
        script: |
          flutter build web --release
    artifacts:
      - build/web/**
    publishing:
      email:
        recipients:
          - moh244415@gmail.com
    max_build_duration: 60
