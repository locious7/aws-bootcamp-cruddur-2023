# Week 0 — Billing and Architecture

Prior to week 0, I went through the prerequisites found [here](https://docs.google.com/document/d/19XMyd5zCk7S9QT2q1_Cg-wvbnBwOge7EgzgvtVCgcz0/edit#heading=h.2kbe0qpj789o). I had 4 of the 9 pre-reqs already setup.

Setup the following:
* Gitpod.io
* Honeycomb.io
* rollbar.com
* https://www.gomomento.com/
* Route53 custom domain


### Notes from Project Scenario Meeting
![image](https://user-images.githubusercontent.com/59851207/218853209-7c569743-80f5-40e9-81de-9c7aca4b25ac.png)

I had previously been using AWS for work and personal projects, so the AWS CLI, budget, and billing alarm was already setup!

### Architectual
* Requirement
* Risks
* Assumptions
* Constraints
* The Iron Traingle = Cheap, Fast, Good


### Diagrams
I created both the Conceptual Diagram and Logical Architectual Diagram via [LucidChart](https://www.lucidchart.com/)
links to diagrams:
* [Crudder - Conceptual Diagram](https://lucid.app/documents/view/800600da-5f30-408a-b8d3-05ef69ee6934)
<img width="1102" alt="image" src="https://user-images.githubusercontent.com/59851207/219844637-d2e2a752-5d43-4a67-b2ba-294858bd9b00.png">

* [Cruddur - Logical Diagram](https://lucid.app/documents/view/4e54e450-f6ce-46eb-8eb3-3a38aa7ef568)
<img width="1219" alt="image" src="https://user-images.githubusercontent.com/59851207/219843911-a23b3fc7-fed3-4f13-b11b-f65264e8b5d0.png">

### Homework Challenge
* Use EventBridge to hookup Health Dashboard to SNS and send notification when there is a service health issue.
* I used the following configuration:
```
AWSTemplateFormatVersion: '2010-09-09'
Description: CloudFormation template for EventBridge rule 'AWSServiceHealth'
Resources:
  EventRule0:
    Type: AWS::Events::Rule
    Properties:
      Description: Send notification when AWS service is unhealthy
      EventBusName: default
      EventPattern:
        source:
          - aws.health
      Name: AWSServiceHealth
      State: ENABLED
      Targets:
        - Id: ######redacted######
          Arn: arn:aws:sns:######redacted######:ServiceHealth
```
