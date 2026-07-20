AWS Essentials
Getting Started
Course Introduction
Hello there, Gurus. My name is Elizabeth Hord. I'm just your friendly
neighborhood metalhead with a soft spot for doggos and 5 AWS certifications. In
this course, we're going to be looking over the things that make your AWS
account essential, the things that can get you off the ground quickly and
efficiently. This isn't necessarily a certification course. But if you want to take your
certification course after this, this can help build a nice groundwork for you. Let's
go over what we're going to touch on in this course. First, we're going to look at
the power of the AWS account, how it works, and how to set one up. Then we're
going to jump into IAM, or identity access management. That controls the who's
who inside your account. From there, we're going to jump into EC2. We're utilizing
Elastic Cloud Compute. We're also going to take a look at the storage solutions,
specifically S3. And then we're going to look at the bubble that holds it all
together, the VPC, or the Virtual Private Cloud, how networking affects
everything inside of the cloud and around it. From there, we'll take a look at
database services, things like RDS and DynamoDB. After that, we're going to jump
into CloudFormation. CloudFormation is a tool that helps you build out your
environment. Specifically, it's really good for automating how you build out your
environment. And then we'll take a look at management tools, all those tiny little
tools that actually make a giant difference in how your account runs. And from
there, we'll jump into security. The main two things we'll be looking at being
Security Hub and GuardDuty. The last thing we'll take a look at is going to be the
conclusion, the wrap-up, and where to go from here. After you finish this course,
what else can you look at? Come along. Let's see if we can learn this together.
The Power of an AWS Account
An Overview of AWS Accounts and the Features of Free
Tier
Hello, everybody, and welcome to AWS Essentials. In this particular lesson, we're
going to be going over what we're going to cover in this section. What exactly is
an AWS account? What is the AWS Free Tier? And what does the Free Tier have
to offer? Let's get started. But before we jump into the lesson proper, let's talk
about what we're going to cover in this particular section. The first thing is this
video. It's an overview of the AWS account, as well as talking about what the
features of the AWS Free Tier are. The second thing we're going to cover is how
to create an AWS account, as well as how to navigate through the console as a
whole. We're also going to cover billing alerts and how that can potentially save
you quite a bit of money when set up correctly. And then the final thing we're
going to cover is AWS documentation, specifically what it looks like and how to
find it. So let's get started in the lesson. Okay, so first and foremost, let's talk
about an AWS account as a whole. And what exactly does that mean? Well, I like
to think of the AWS account kind of like the hull of this ship here. Without that
hull, you really don't go anywhere. So realistically speaking, without the
account, you wouldn't really be entering the cloud computing space as a
whole. And this is true of most cloud computing companies. You need an account
in order to access resources and things like that. This particular course will be
focusing on AWS, but this particular case is true for just about every cloud
company. The thing that is also good about AWS accounts as a whole
is everything they have is in one particular place. You find all of their stuff
through the console. Now, you can access things through different methods, but
realistically speaking, everything is available for you to see. Even if you have
multiple accounts, you can still use AWS organizations to have it all listed in one
particular console, which could be really useful if you're not used to flipping back
and forth on things. So I'd like to talk about AWS's Free Tier now. Specifically, AWS
has a plethora of services that falls under the umbrella of AWS's Free Tier. But
when you break it down, realistically, they have about four categories that
everything really falls into. The first is free with some soft limits. Specifically, they'll
have a set limit for that specific service for the first 12 months of your
account. Things like you get 5 GB of free storage space in S3 or a certain number
of hours for a certain type of instance in EC2. The second category is services
that are always free. The first million requests with AWS Lambda or the first
million notification requests through SNS. Those things are always free even after
you hit that 12-month mark. The third option is services that are specifically
offered on a trial basis. So it's a trial that's smaller than that 12-month limit like you
saw with the free with soft limits. Things like Security Hub or GuardDuty
specifically offer a 30-day free trial of that particular service. And then finally, you
have services that are free, but you can upgrade them if you want different types
of service. AWS Trusted Advisor allows you to have certain specific checks that
are available for your environment. However, if you want to get a little bit more
nitty gritty in your environment, you can always upgrade your service to
something a little bit higher. Now, like I said before, there are a plethora of
services that are specifically offered under the AWS Free Tier umbrella. I'll be
leaving a link in the resources section that will specifically take you to the page
that talks about this in AWS's documentation. I would really highly recommend
that you look through that documentation, specifically as, although I'll be
covering a lot of things in this course, there might be something in that list that
might be considered essential to your business needs that might not be
considered an AWS essential. And with that, let's have a quick review of what we
touched on in this particular lesson. The first thing we covered was what we're
going to cover in this section as a whole. The second thing we covered is the
power of an AWS account as a whole to try and get you into that cloud
computing space. Then we talked about what the AWS Free Tier is and
more specifically what it has to offer you. I hope this cleared some things up, and
I look forward to seeing you in the next one.
Learning How to Create an AWS Account and Navigating
through the Console
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over how to create an AWS account, how to navigate into the
console, and how to get into the cloud sandbox from ACG. Let's get started. So,
creating an AWS account. Realistically, this is only a three-step process. First, you'l
l navigate to the AWS website, then you'll fill out the account form, then finally,
you'll confirm your email address, and you have your nice, shiny, new AWS
account. Okay, it's demo time. Let's go look at how to make an account, how to
navigate in the console, and how to open up the sandbox from ACG. I'll see you in
a bit. All right, Gurus, and welcome to the AWS home page. So from this page, we
are going to create an AWS account. So we're going to click Sign in to the
Console. And then we're going to go down here and click Create a new AWS
account. From the screen, we just need a root email address and then an account
name. So I'm going to use a temporary email address. Then for account name,
we're going to put Example. Then we click Verify email address. This is what the
email will look like. I'm just going to type in the code here. Then we click Verify,
and the email has been successfully verified. So here's where we make a root
password. So it has to be at least 8 characters long and needs to have three of
the following, an uppercase letter, a lowercase letter, a number, and a non-
alphanumerical character. So I'm just going to type in a password, and I usually
try to hit all four of the bubbles just to be sure. Then we say Continue. So now we
need to put in our information for this account. We're going to go ahead and say
it's a personal account. I'm going to put in my name, Elizabeth H, Phone Number.
Then we've got our address, UT, and our zip code. Agree with the terms of service.
And then here is where we'll have our credit card information. I'll go ahead and do
this offscreen, and then we just add our mobile number again. Do the captcha
here. Then it will send us a security code. Then we're just going to type that
security code in. Hit Continue, and we're going to leave this as a Free Tier
support, though you can go to one of the other two if you think that's necessary
for your business. And then we're going to hit Complete sign up, and we've
activated our account. So now we can go ahead and click on Go to the AWS
Management Console. Then we paste our email address, put in our password, and
now we have successfully logged into our AWS account. So from here, let's talk
about how to navigate around in the AWS account. So, we can go to any of these
sections to get more information specifically about AWS. What's new will talk
about any new services or features. Getting started will help you with some
fundamentals, specifically some whitepages. Training and certification, if you
choose to take the certification route, we highly recommend looking into some of
these options, as well as watching some of the videos here on ACG. You're also
going to have a generalized selection of options here in the Recently visited
section, even though this is a new account. You also have this section up
here, which is going to be basically your home screen where you have options
to click on for quick access to another part of the console. So, let's say we want to
add EC2 to that section. What we can do is from the search bar, type in EC2, hit
this little star button here, and it pops up right here on the search bar. So now we
can get to EC2 by just selecting this little button here, and there we have it. We're
in the EC2 section of the console. You can also use these buttons to go, instead
of just from the home page, you can use them just about anywhere. So, since
we're in the EC2 section of the console, let's go ahead and click on the S3 section
here. And as you can see, it's brought us to the S3 section of the console. All
right, so the last thing on our list is going to be opening a sandbox from the ACG
panel. Okay, so from the A Cloud Guru platform, we have an option called
playgrounds. So we're going to click on Playground. And in this playground, you
see that there are options for sandboxes. These sandboxes are basically your very
own AWS account. They do have some limitations for things like IAM and some
security preferences for obvious reasons, but they can be really useful if you're
just trying to get a little bit more hands-on experience. So we just click the Start
AWS Sandbox, and we have a user, password, as well as a URL and some access
keys that we can use for this particular sandbox. So in order to get to the
sandbox, we're going to right-click on Open Sandbox. Select Open Link in
Igcognito Window. The IAM user is going to be cloud_user. Then we copy the
password. Go back to the sign-in page. Paste and sign in. And there we have it. As
you can see, we have a cloud user sandbox. That way you won't have to use any
credit card information or anything like that. Like I said before, the sandbox is a
really good feature specifically for ACG students. It allows you to really get some
hands-on experience without having to worry about the cost associated with an
AWS account. And with that all being said, let's head back to the slides so we can
take a recap of what we learned in this lesson. And welcome back. Let's go over
what we touched on in this lesson. First, we talked about how to create an AWS
account. Then we talked about how to navigate through the console and how to
open up the sandbox in ACG. I hope that cleared some things up, and I look
forward to seeing you in the next one.
Leveraging Billing Alerts
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over billing alerts, what they are, why you would use them, and how
to set them up. Let's get started. So, billing alerts, what exactly are they? A billing
alert monitors your environment to make sure you're not spending more than
you really want to when it comes to your resources. It also allows you to set a
budget to let you know when you're getting too close to a certain percentage
that you don't want to spend in your environment. Let's now talk about why you
might use billing alerts. The first thing that I want to bring up is security and
peace of mind. With budgets and billing alerts, that means you aren't going to get
a surprise bill that's higher than you want to pay. It also means that you always
know what's going on with your account when it comes to costs, specifically with
the notification system. All right, it's demo time. Let's head over into the console,
and I'll show you how to set up some billing alerts. I'll see you there. And welcome
to the AWS console. So from the console today, we're going to be setting up a
budget and then setting up a billing alarm. So if you don't have it in your recently
visited or if you don't have it in your search bar up here, the easiest way to find it
would be going up to the search bar, typing AWS Budgets, and click on AWS
Budgets. So from this page, we're going to create a budget, specifically so that
we get alerted if our account goes over a certain price point. As you can see
here, it's saying, hey, your pricing is currently set to US pricing. This can obviously
change, depending on whatever region you're in. But for me personally, it's going
to say US. We're going to go ahead and create a budget, and we're going to go
ahead and say Use a template. It's a simplified version of this. So there's a couple
of options when it comes to what templates you can use. You can either do a
daily savings plan. So basically, if you had a specific number that you were trying
to hit every day, then you could click on this button. You could also do a zero
spend budget if you're just trying to get stuff out of the Free Tier. That's a really
good option if you're just getting started with AWS and you just want to try things
out. Setting up a zero spend budget is really helpful. There's also the monthly
cost budget. Hey, you've set a certain amount, and if it goes over that
amount, we'll let you know. That's the one I'm going to click on today. I'll click on
Monthly cost, go down to budget, and I'm going to make it $20. Now, it needs an
email. Let me grab that really quick. There we go. So you would just put your
email in here, and the scope is All Aws services, so whatever your spend is. And
with this particular template, you'll be notified if your actual spend reaches 85%
of your budget. You'll also be notified if your forecasted spend is expected to
reach 100%. So now we're going to go ahead and click Create budget. All right,
my monthly cost budget, it currently says my threshold is okay, so I'm not
spending $20 a month. It says my budget is $20. The amount used is $0. My
forecasted amount to spend is going to be $0.03. So let's go ahead and go and
make that alarm now. So how we can do that is we can go over to CloudWatch.
Type in CloudWatch. Click on CloudWatch here, and here is the CloudWatch
portion of the console. So from here, we're going to go over to Billing. And as you
can see, we currently don't have any billing alarms set up, so we're going to
create an alarm. The Metric name is going to be EstimatedCharges, and I want it
to be greater than, let's go greater than 15 USD. And we'll say, and then we'll hit
Next. We'll send it to our topic here, which means it'll send out an email. Then
we're going to hit Next. So for Alarm name, we're going to say Spend over $15. Hit
Next. So this is going to be the preview of it. And as you can see, our estimated
charges are still at 0, so the alarm isn't going off. Go ahead and Create alarm, and
there we have it. We have our billing alarm set up for our spend over $15. Let's
head back to the slides so we can look at everything we touched on in this
lesson. I'll see you there. And welcome back. Let's go over what we touched on in
this lesson. First, we talked about what billing alerts are. Then we talked about
why you might use them. And finally, we jumped into the console to take a look
at how to set up billing alerts in practice. I hope this cleared some things up, and I
look forward to seeing you in the next one.
AWS Documentation: What It Is and Where to Find It
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about AWS documentation, what it is, why you might use it, and
where to find it. Let's get started. Okay, so what is AWSdocumentation? AWS
documentation are called whitepapers. They are very detailed instructions for
just about every service that AWS has available. AWS whitepapers are written by
incredibly talented technical writers who have a particular gift for
making complex ideas easier to understand. The whitepapers also have entries
for just about every service you can think of, specifically from their big services
like EC2 to much smaller services like AWS translation. So now that we know what
the documentation is, let's talk about why you might utilize it. The first reason I
would give is that AWS is constantly growing. And as new services get added, new
information is provided about those services, which can be really useful for
growing your business needs. The other reason I would give is that changes
happen within the services that AWS currently has. As AWS continues to grow
and add new services into their catalog, they're also constantly doing
maintenance on the services they currently have, which means sometimes you
might get UI changes or even something as simple as a particular output that you
were expecting from a service has changed where it is in the console. These
changes are always written up in the whitepages, which is why it's a really good
idea to take a look at those to see if there's been any updates on those pages for
services that you utilize usually about once a month. All right, it's demo time. So
now that we know about the what and the why, let's get started on the where you
can find AWS documentation. I'll see you there. And welcome to the AWS
console. So from the console, there are a couple of ways to get to the whitepages
for AWS. Realistically, you'd be looking at this section here, this Welcome to AWS
section. Getting Started with AWS is probably your best bet. Though, if you are
looking for training and certificate information like specifically, if you're thinking
about going for the Solution Architect exam or the Cloud Practitioner exam, this
might be one of the best places to go, but let's get up to Getting Started with
AWS. So from this page, it'll explain in a little bit of detail what exactly AWS is, as
well as some of the specific fundamentals that they believe that you should
know. But the other thing that it will do is it will get you to the document section
of the page, and here is the AWS Documentation section. They have
documentation on just about everything you can possibly think of. All of their
services have a specific document page they are going for from their big stuff like
RDS to their little stuff like Amazon Polly. The other way to get to these types of
pages would be to try and Google the page, typing in AWS and the service name
that you're looking for. So, like aws, space, sns documentation, and it would
take you to this page. Realistically speaking, if you're wanting to get specific
information on this service, like say we wanted specific information about SNS,
you can either search for that particular issue here, which is search within this
product, or you can go straight to the developer guide, and it can give you a
more detailed lookout of what this particular service does, how it works, and what
services it interacts with. Let's head back to the slides and take a look at what we
covered in this lesson. Welcome back. Let's go over what we touched on in this
lesson. First, we covered what AWS documentation is. Then we talked about why
you might utilize AWS documentation and why it's a good idea for you to look at it
about once a month. And finally, we explored where to find AWS documentation. I
hope that cleared some things up, and I look forward to seeing you in the next
one.
Identity and Access Management (IAM)
Discovering What IAM Is
Hello, everybody, and welcome back to AWS Essentials. In this video, we're going
to be talking about what we're going to be covering in this section and an overall
picture of what IAM is. Let's get started. So in this section, we're going to be
talking about IAM, what it is, how to provision it for the first time, creating users,
groups, and policies, and finally, establishing IAM roles. So, let's talk about what
IAM is. IAM stands for identity and access management. In relation to the ship
here, we're looking at the main entrance. IAM controls who can do what and
where. Using IAM is the best practice for security as you can make sure people
who are working on your account only have access to what they really need
to have access to. It also allows for services to interact with each other with the
information that needs to be looked at. Okay, let's go over a quick wrap-up of this
particular lesson. In this video, we touched on what exactly we'll cover in this
section and an overall picture of what IAM is. I hope that cleared some things up,
and I look forward to seeing you in the next one.
Provisioning IAM for the First Time
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to cover what it looks like when you first open your AWS account. specifically in
the IAM space. We're also going to go over what to do when you first open your
account, including turning on MFA and locking down that root account. Let's get
started. Okay, so first things first. Let's talk about multi-factor
authentication. Multi-factor authentication, or MFA, is the concept of having
extra protection when you log into any service like your email or your
favorite shopping sites. It allows you to make sure that people aren't
accessing your account that really shouldn't. It's also considered to be a best
practice when it comes to AWS user accounts to have MFA active. So now that
we know about MFA, let's talk about why you should absolutely secure your root
account for AWS. There are three things that you really need to consider
when you're going to lock down that account. The first thing is access keys, the
next is incorporating really strong passwords, and finally, it's incorporating multi-
factor authentication. So first and foremost, when you're dealing with access
keys, access keys allow you to have programmatic access into your console. In
other words, you can use your command line to do tasks. Generally speaking, it's
a good idea to not have access keys on your root account at all as it's a huge
security risk and can potentially be much easier to get into. But if you do need to
have access keys for your root account, make sure to change them monthly. So
that way you can be sure even if there is a leak, it definitely won't stay there for
long. The second thing is having strong passwords. These standards can change
per account. But generally it's recommended that you have a minimum of eight
characters, including letters, numbers, and symbols without it being a date or
address of some kind. And finally, you have MFA. Enabling multi-factor
authentication on your accounts can be incredibly important to your overall
account health and security. All right, it's demo time. Let's jump into the console
and see this process in action. I'll see you there. Hello, everybody, and welcome
back to the AWS console. So in the console today, we are going to be taking a
look at securing our root IAM account through the console. So if you don't have
IAM in your Recently visited and you don't have it on your little bookmark border
up here, the easiest way to get there is to be going up to the search bar, type in
IAM, and click on IAM. Okay, so as you can see here, this is our security
dashboard. And you can see that it's saying, hey, MFA is not currently accessed
to the root user, but your root user has no access keys, which is really good. So
let's add MFA. So we're going to click on this button here, and we're going to click
Activate MFA. Doing a virtual device means that it's an Authenticator app usually
on either your cellphone or on your computer. You can also do a security key if
you have a specific device kind of like an RSA token. Or if you have some other
type of hardware device, you could always use that as an option here. We're just
going to stick with Virtual MFA for the moment. So essentially how you would do
this, you'd click on Show QR code, scan the QR code with a cellphone or other
device. Once you scan the QR code and open in whatever Authentication app
you want to use, you then will type in whatever numbers you have. And then the
second one, as we just wait for it to time out and bring up a new code, and we
click Assign MFA. And there we have you successfully assigned your virtual
MFA. We go ahead and click Close. So if we had access keys, like I said in the
slides, it's not the best idea to have these particular things on your root
account, but you can have them. So, you can click Create New Access Key,
Download Key File, Close. Now once you have that access key, you can either
make it inactive or delete the key. I'm going to go ahead and delete it. We just
copy and paste the name of the key after clicking Deactivate and then Delete.
And now it's showing the Status as Deleted. So if you're wanting to change your
password, you're able to do it through this screen. So under Account settings, we
can always change the password policy like we talked about in the slides. So we
can enforce the minimum password requirement. Right now, it's set to 8. And
we're going to require at least one uppercase, one lowercase, one number, and
one non-alphanumeric character, which would be any of these guys here. You
can also set a password expiration, which means that you have to specifically
change your password in every specific set of days. It defaults to 90. You also can
set it so that if a password does expire, it requires an administrator to reset it, or
you can set it so that your users can change their own passwords. You can also
make it so that you can prevent password reuses. So specifically, if you had
sensitive data or had a governmental body that's looking into these sorts of
things with specific structures for your passwords, you can always set that up
here to say, hey, you can't use the same password as the last five passwords you
have used. It forces people to be a little bit more creative, thus a little bit more
secure. Then you would just go to Save changes. You would have your new
updated realms right here. And with that covered, let's head back to the slides to
review what we went over in this lesson. I'll see you there. And welcome
back. Let's go over what we touched on in this lesson. First, we discussed what
MFA is. We also discussed how to secure your root account in theory. Then we
jumped into the console and secured it in practice. I hope that clears some things
up, and I look forward to seeing you in the next one.
Creating Users, Groups, and Policies
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about creating users, groups, and policies, what's the difference
between those three things, and what ways you might customize your
particular options when utilizing all three of them. Then we're going to jump into
the console and take a look at all three in practice. Let's get started. Okay, so
users, groups, and policies, what exactly are the differences? So, first and
foremost, when you're looking at users and groups, we're looking at
identities, things that can identify a person in your account like Bree from HR or
Tina from IT. You have the users, Bree and Tina, and their groups, HR and IT. Then
you have policies. Policies control the actions the identities can take. So Bree
from HR will have access to a specific S3 bucket, something that looks at the pay
scale for the company, while Tina has access to things like EC2, CloudWatch, and
other services needed for her job. So, why would you use different users in your
account? The first and foremost reason would be for security. These individual
users allow you to track who's doing what inside of your account. The other
reason would be easier maintenance tasks, things like allowing users to change
their own passwords and having specific contacts for notification purposes. That
way you don't have Bree from HR getting emails that, hey, this particular
autoscaling group isn't functioning correctly. She doesn't really need to know
that. But Tina from IT definitely does. Okay, so now that we've covered users, let's
talk about groups and why it's important to have different ones inside of your
account. Once again, first and foremost, it's about that security. Having your
teams being separated into groups means that you can invoke least access
privileges. So that way, you don't have people that have access to things that
they really don't need to. There's also the efficiency factor to take into
consideration. Another reason to have multiple groups depending on your
teams would be that you're getting a new person or you're rolling new people
into your team or changing job roles. All you would need to do is add that person
to the group of that team, and suddenly they have all the permissions necessary
to accomplish the tasks they need to. So with identities out of the way, let's talk
about why you would use custom policies. Realistically, you would use custom
policies with your groups and users to dictate what they have access to. Normally
speaking, you would have inline policies for users and overall policies for
groups. It's considered best practice for you to use your overall policies in groups
rather than inline policies for a specific user. All right, it's demo time. Let's head
into the console and take a look at the differences between users, groups, and
policies in practice. I'll see you there. And welcome to the AWS console. So, we're
going to talk about IAM, or identity access management. Now we need to get to
that particular side of the console. Now if you don't have these convenient
buttons on your home page, you can always find the IAM side of the console by
going up to Search, typing in IAM, and then hitting Enter. Okay, and we are at the
IAM home page. So let's talk about what we see on this page. We see that multi-
factor authentication is not currently set up for the root user nor is it set up for
the current user, which I'm on one of the cloud user accounts. Now I do have an
access key for this cloud user since I'm using one of the sandboxes available to
us, but we're also going to look down here at the IAM resources. So from here, we
can see that there is currently 1 user group, 2 users, 46 roles, and 2 policies. Also,
when it says policies, it means customized policies. So the first thing that we
should have a look at is this Users section. So as we can see here, there are
currently two users. One of them is Bree, and one of them is the cloud_user. Now
let's say we wanted to make a user account for Tina, who's on our IT team. How
we would do that is we'd click on this Add users button, and then we would type
in her name, Tina. So here's what type of access Tina would have. Access keys
allows her to do things with the CLI and the API, as well as using other developer
tools. And considering Tina's on our IT team, we definitely want her to have
programmatic access. So we're going to click this little checkbox, but we also
want Tina to be able to log in with a password since she's also going to be
managing things like our EC2 environment and our CloudWatch environment. So
we click on the Password button here. So as you can see, when it comes to your
password, it'll give you a couple of options. You can either auto generate your
password, or you can set a custom-specific password. Also, it's considered best
practice for you to keep this little box checked. That way, your user has to reset
their password when they log in for the first time. I'm going to go ahead and keep
it as autogenerated, and I'll go ahead and keep this box checked. We're going to
hit Next. So here's where we can add permissions to this particular user. We can
either add them to a group, or we can copy specific permissions from an existing
user. So we could potentially give her the same access that we have as the
cloud_user, or we could keep it as whatever Bree has. There's also an option to
add policies specifically to this user. Now it's usually not the best idea to add
specific policies to the users, as generally speaking, that can lead to holes in your
security. So let's go back to Add user to group. And as you can see, we currently
have one group that's called IT. So we're going to go ahead and click on that. The
policies for the IT group are the AmazonEC2FullAccess policy, full access to
CloudWatch, and full access to SNS topics. That way they can make sure that
notifications get sent out correctly. Next we go into tags. This would be a good
place to put things like your manager structure or who this person is particularly
involved with, or if you have multiple organizations using the same account, that
also might be a good idea. Say, like Tina works for Company A and Bree works for
Company B. Adding Company and the name will help differentiate which user
works for what company. Okay, and here's the review section where we take a
look to see what we're going to make for our user. So our username is going to be
Tina. They have Programmatic and Management Console access. It's going to be
an auto-generated password. And it's going to require a reset, specifically when
they log in for the first time. And the only inline policy they currently have is
that they can change their own password. We're going to go ahead and click
Create user, and there we have it. We have our user Tina. This would be her
access ID, the secret access key, which she'll need for things like using the
Amazon CLI and using other development tools. This is also going to be her
password, which she'll have to change when she first logs in. And we can see
here what exactly happened in the build-out process. The console created the
user Tina, attached the policy, created an access key and a login profile. Now
there are two ways you can get this information to Tina so that she can log into
the console and start doing work. One of the options would be to send an email
to her, which will give you a set of instructions saying, hey, here's how you can log
in, here's your information. The other option is downloading this CSV file. Now the
CSV file will look like this. It'll specifically have her username, her password, access
key, her secret access key, as well as what her login link will be, specifically when
she goes to log into the console later. So, with that out of the way, we're going to
hit Close. Now as you can see, we have the user Tina, who is in the IT group. And
her user was created 2 minutes ago. So let's say you had a new bucket that you
have to have HR take a look at. We really want Bree to be a part of that
group. How we can create a group is we'll go up to User groups, Create
group. Now, we're going to name this group HR. And then we're going to add Bree
to it. Now Bree doesn't really need access to just about anything except for some
S3 buckets. So there are some options for her to do. If it's specifically she just
needs to look at information inside of S3, we can put the S3ReadOnlyAccess,
meaning that they can look into the S3 bucket, but can't make any changes to
it. Or we could give them full access if they would need to edit and create
buckets as well. So, we're going to hit this Create group button. All right, and as
you can see here, the HR group has been created. And there is one user currently
in it. You can also see that here. The user for this group is Bree, and the user for
this group is Tina. Now, let's say we want to add a specific policy to one of these
groups. But we wanted it to be a little bit more customized than the options that
we have here. Well, how we can do that is we're going to go to Create policy, then
we choose a service. Let's say that Bree, unfortunately, deleted an S3 bucket that
they weren't supposed to. So now we need to edit what types of buckets she has
access to. So what we would do is we'd scroll down this list, go to S3. So we want
to be able to list and read. So we want her to be able to write, but we don't want
her to be able to delete anything. So we just check off these buttons that say
Delete. If we were going to have this set to a specific bucket and were going to
really restrict where it was going, you could just add the information for that
particular bucket, the specific name for that bucket here and make it so that
they could only do these tasks to that specific bucket. Same thing with the
objects inside of those buckets. You would add the bucket name here and then
the object name here and then go from there. In this particular case, I'm going to
go with Any since we aren't letting her actually delete anything, and everything
else should be fine in this case. So next, we're going to go to tags. I'm going to go
ahead and leave that off for now. And now we need to name our new policy. I'm
going to name this Updated-HR policy, a Least permissioned policy for S3. All
right, and we're going to go ahead and click Create policy. All right, the policy,
Updated-HR, has been created, and now we'll have to go and add that into our
group. So we're going to go back up to User groups, click on HR, and then we're
going to go to Permissions. So the first thing we're going to do is remove this
S3FullAccess permission. We click on the checkbox, click Remove. All users in the
group will lose permissions as defined in this policy, and we want to do that, so we
hit Delete. And now we're going to add new permissions. And we're going to
attach policies. There is our new policy that we just made, the Updated-HR
policy. Add permissions, and there we have it. Now HR only has access to put
things into buckets, but can't delete them. All right, with that all covered, let's
head back to the slides to wrap up. I'll see you there. And welcome back. Let's talk
about what we went over in this lesson. First, we discussed why you would use
users, groups, and custom policies and the differences between all these
options. Then we jumped into the console to take a look at these three options in
practice and see how they work. I hope that clears some things up, and I look
forward to seeing you in the next one.
Establishing IAM Roles
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over what IAM roles are, what the differences between identities,
policies, and roles are, and then jumping into the console to take a look at them in
practice. Let's get started. So, IAM roles. What are they? IAM roles, much like
policies, allow you to choose what services users have access to. But they also
allow other services to have access to each other. So if you wanted your EC2 to
be able to access your S3, which is AWS's virtually unlimited storage service, you
can set a role to have that particular property. They also allow users to have
temporary action tasks. They also allow users to have temporary access to
things. So if you don't want to normally associate a user with a particular task, but
you want them to have access for this particular reason for this particular day, you
can add a role to that particular user and then take that role away without
changing their overall access or having to go through the process of changing
their access. Okay, so users, groups, policies, and roles. What's the difference? So,
users and groups fall into the category of identities. They're the specifics for
logins, either a group like Bree in the HR department or Tina in IT. But you also
have those users, Bree and Tina, that are able to log in, as well as their groups, HR
and IT. And then you have policies. Policies are specifically the permissions of
these individual identities, either users or groups, that tell you what you can and
can't touch. So things like you want Bree to have access to S3, but you need Tina
to have access to just about everything. And then there's roles. Roles allow users
and services to have access to each other, and they can be temporary. So that
way, you can have this particular user having access to this particular device. Like,
for example, if you wanted Bree to have access to a particular S3 bucket or
a specific EC2 instance to pull a report, you can set a role for her to allow her to
do that particular action and then take the role off once she has completed that
action. All right, it's demo time. Let's take a jump into the console and take a look
at roles in practice. I'll see you there. Okay, so welcome to the IAM dashboard. We
currently have 2 user groups, 3 users, 52 roles, and 6 policies. So let's go over to
Roles really quick. So as you can see, in Roles, we have a lot of AWS services.
Roles in AWS really shine if you want AWS to call on a service for you. So let's say
we have a lambda function that needs to ping an EC2 instance, but we don't
have a role for that. So what we can do is we can go up to Create role, AWS
service, Allows EC2 instances to call AWS services on your behalf, Allows
Lambda functions to call AWS services on your behalf. So we're going to click
Next. Now, we want our lambda function to be able to call EC2s. So we're going to
type in Ec2, and we're going to give it the EC2FullAccess. Then we're going to hit
Next. We're going to type in Function Test, and then we're going to click Create
role. Creating the Function Test role. And if we type in Function, there we have
it. We have Function Test. The trusted entity is going to be the lambda
service, and it has the activity of being able to call EC2 instances. Let's head
back to the slides so we can go over what we touched on in this lesson. I'll see
you there. And welcome back. Let's take a look at what we touched on in this
lesson. First, we talked about what exactly an IAM role is. And then we talked
about the differences between identities, policies, and roles. And then finally, we
jumped into the console to see what these look like in practice. I hope this
cleared some things up, and I look forward to seeing you in the next one.
Utilizing Elastic Cloud Compute (EC2)
An Overview of Elastic Cloud Compute
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over what we're going to cover in this particular section, as well as
looking into what exactly EC2 stands for and what is EC2 as a whole? Let's get
started. But before we jump into lesson proper, let's go over what we're going to
be covering in this section as a whole. So in this section where we're talking
about utilizing EC2, the first thing we're going to cover is this video, what exactly
is Elastic Cloud Compute, or EC2? We're also going to be talking about
understanding the basics of EC2 and how it works. We're then going to be talking
about Amazon Machine Images, or AMIs, and why those are important. We're
going to talk about understanding EBS, or Elastic Block Storage. We're also going
to be talking about security groups. Then we're also going to be talking about
auto scaling and how it works, specifically how it works with EC2 and why it's
important. We're also going to be talking about associating IP addresses, defining
resource groups and tagging, what are Elastic Load Balancers and how do they
play into all this? How to create and utilize an EC2 instance, how to connect to an
EC2 instance, how to install software on them. And then finally, we're going to go
over a quick review over what we covered in the previous sections. So, let's get
started on the lesson proper. So, EC2 stands for Elastic Cloud Compute. And
when you think about it, I want you to think of the main rocket of the shuttle. That
particular rocket helps propel the shuttle into the atmosphere. It's like that for
EC2. EC2 is one of the backbone services of AWS, so it's considered essential. The
other thing is when you're dealing with EC2 as a whole, you're utilizing cloud
compute technology. And when you utilize cloud compute, that means that
you're taking hardware in one place and utilizing it somewhere else. But let's get
into a little bit more nitty gritty on how that works. So this is what a server rack
looks like. And each of those big, black boxes, there are anywhere between 5 to
20 servers. And a server is basically just a really, really beefed up computer. A
server is connected to the internet, so it can send information or user data over
the internet to a client or a person logging into it. Normally, you would need a
connection to go from that server into your client machine or, in this case, a
laptop. With an EC2 being a virtual server, that means you don't have to have a
dedicated room on-premises for those big, bulky computer racks, and you can
just have them in the cloud, which can be really, really handy for startups or small
businesses. Okay, so let's review what we covered in this particular lesson. First,
we talked about what we're going to cover in this particular section. Then we
discussed what exactly is an EC2. And then we talked about some of the reasons
that you would use an EC2 over your standard server rack. I hope this cleared
some things up, and I look forward to seeing you in the next lesson.
Understanding EC2 Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over the basics of EC2, the different instance purchasing categories,
as well as the different instance types. Let's get started. EC2 instances are like
the main rocket. It's the flagship and the driving force of most AWS accounts. It's
incredibly customizable with three different categories and plenty of different
types to choose from. You also only pay for what you use, so you don't have to
worry about weird costs or unusual pop-ups on your bill. So let's talk about the
main different purchasing categories of EC2. There are realistically three different
options, on-demand and per second, saving plans, and spot instances. These
three categories allow you to customize your environment to be exactly what you
need it to be. With per-second style of instances, you're dealing with more of a
dedicated space. You have a price that you pay for the instance per second. While
this is the most expensive option, it's also the most useful if you're still getting a
feel for what your environment needs. Next, you have saving plans. Saving plans
allow you to pay up front for the EC2 needs and usages that you'll have. Normally,
you can get a much better price than the per-second cost. However, you are in a
contract for however long that you're going to use those EC2s, which can be
really helpful if you already know what your environment needs and you have
your longer term usage planned out. Finally, you have spot instances. You can get
a huge discount when it comes to bidding for these particular style of
instances. Instead of paying a price per second or paying upfront pricing like you
do for on-demand or saving plans, spot instances allow you to bid for a
specific pricing that you want to pay for your instance. However, if the price for
that instance goes outside of what you originally bid, that means that it'll shut
your instance off. Spot instances are really great for things like short-term work or
things with flexible start and stop times. Okay, so let's discuss the types of
instances you can use since we've just gone over the categories. The first type is
the one you'll see probably most often. It's the general purpose type of
instances. These instances come with a balanced approach for your everyday
tasks. So you don't need the spikes of the other types. General purpose instances
are generally an all around good choice for most everyday tasks. Next, we have
the accelerating computing instance. This instance type is really designed with
design work in mind. The ability to add hardware to help compute speeds and
load, it allows you to do way more intense tasks than a general purpose
instance. Generally speaking, these are the types of instances you'd use for
AutoCAD or developer-heavy tasks. Now we're jumping into the optimized
section of the types, and we're starting with the compute optimizations. With
compute optimizations, you're always looking at the heavy media load, things like
video transcoding or multimedia projects. That's really where the compute
optimized instances shine. Next, we have the memory optimization, which allows
your RAM to shine through. Normally, this type of instances is really good for
dealing with big chunks of data or huge organizational information. And finally, we
have storage optimization. This type of instance is great for things that require a
lot of storage space or for things that require you to have a consistency for a long
period of time, things like compliance reports or specific information or data that's
needed by regulatory bodies. All right, it's time for a review. Here's what we
touched on in this lesson. First, we discussed the different purchasing categories
you can have for instances. Then we talked about the different types of instances
and where you might use them. I hope this cleared some things up, and I look
forward to seeing you in the next one.
Reviewing Amazon Machine Images (AMI)
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be reviewing Amazon Machine Images, or AMIs. Specifically, what are they,
how do you use them? And then we'll jump into the console to take a look at
them in practice. Let's get started. So, Amazon Machine Images, what exactly are
they? Well, the first and foremost reason that you would have an AMI is for
backups. AMIs allow you to have quick and easy backups so that it has a
faster response time if something goes wrong in your environment. They also
help you curb costs, so you only save what you need. And also if you ever have an
instance that you only need for a small period of time, having an AMI allows you
to not have to go through the process of installing software or other processes
that might take extra time in order to accomplish. A simple AMI allows you to just
boot up the instance, do what you need to do, and then shut the instance down
and not get charged for it. So, how exactly do you use an AMI? The first thing
that you should be aware of is consistency. When you're using an AMI, you're
specifically having a very consistent environment, assuming that you're using the
same AMI for each of your instances. That means that if you're using AMI A to roll
out your instances, that means all of them will have the same settings and the
same issues. But if you have AMI A and B, that means you have quick and easy
access to switching between AMIs 1 and 2. It's also a really good way for you to
take a snapshot of your environment as it goes through the build process.
Specifically as you're building out your environment and as you're
making changes to your environment, you can have quick and easy access to
changes that you make throughout that process. So let's say that you are
implementing new code, but you're not sure if it's going to work or not. Taking a
quick snapshot of that EC2 instance before you implement that new code means
that if that code doesn't work, instead of having to create an entire new instance
and roll out exactly what you need on it, all you need to do is click on that
snapshot, open it back up, and you're back in business. And of course,
easy backups. With snapshots and AMIs, you're really looking at some quick and
easy backups, so that means that there's no reason for you not to do it. Backups
are really important for keeping your environment healthy and consistent. All
right, it's demo time. Let's take a jump into the console and see what we can work
on from there. I'll meet you there. Hello, everybody, and welcome back to the
AWS console. In this demo, we're going to be specifically looking at AMIs,
how they work, and how you use them. So in order to get there, we're going to go
to the EC2 section of the console. So if you don't have it in your Recently visited
or in your toolbar up here, how you can get there is go up to the search bar
here, type in EC2, click on EC2. And now we're going to launch an instance. I
know you've seen this particular process before, but just stick with me for a
moment. So we're going to go down here to Launch instance, and then we're
going to go to Launch instance again. So from here, when you go to launch an
instance, that's where you can choose your AMI. So we're going to call this a
Webserver, and we're going to click Amazon Linux as our option. But as you can
see, there are plenty of other options available in the Quick Start menu, as well
as quite a few that are available just through the marketplace. So we're going to
stick with Amazon Linux today. We're going to stick with the t2.micro, and we're
going to create a new key pair. Demo is going to be the name of it, Create key
pair. All right, then we're going to allow SSH only from My IP because all of those
are best security practices. Then we're going to click on Launch instance. Now
this process, again, can take a little bit of time. But once the instance gets
made, we'll go over how to create a snapshot with an AMI. So let's click on View
all Instances, and we'll wait until after this is out of the pending state. Okay, so
from this page, how we can make sure that we have an image for our
process, we're going to go down to Image and templates, and then we're going to
create an image. Image name is going to be Backup, and then we're going to click
Create image. All right, so with that, we are creating an AMI. So we have an AMI
listed here, AMI name is Backup, and we've got the source, as well as
what platform and what type of device it is. So with it marked as available, we're
going to go ahead and copy this AMI, then we're going to go back to
Instances, Launch instances, and now we're going to type in our AMI. And as you
can see, we've got our backup AMI here, and it changes our AMI up there. So that
way, we can always have that backup of our instance, just like we originally made
it. Also, if you go into the AMI section and want to make a new instance from
that, you can also just click the Launch instance from AMI, and it'll do the same
thing, giving you all the information that you have on your AMI, as well as this is
the steps that you normally have for your other instance. I hope that cleared
some things up. Now let's head back to the slides to finish out this lesson. I'll see
you there. And welcome back. Let's take a look at everything that we touched on
in this lesson. First, we touched on what exactly is an AMI. Then we touched on
how you might use an AMI. Then we jumped into the console and see how you
use it in practice. I hope this cleared some things up, and I look forward to seeing
you in the next one.
Understanding Elastic Block Store (EBS)
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about Elastic Block Storage, what it is, and what the different types
of volumes are and the wonders of snapshots. Then we'll take a jump into the
console to see how to create an EBS volume and how to attach it to an EC2
instance. Let's get started. So what is an EBS? EBS stands for Elastic Block Store,
an attachable storage for your EC2 instances. It offers you flexible storage to
attach to different EC2 instances with options for easy encryption to keep your
data safe and secure with a simple click of a button. So let's talk about the
differences between solid-state drives, or SSDs, and hard drives, or HDDs. The
first thing we're going to cover is general purpose SSDs, which is the main type of
hard drive that you'll be utilizing. It's the lowest cost for SSDs, but still the most
utilized for things like virtual desktops and small-scale applications. You also have
high performance SSDs for larger workloads and mission-critical workloads. Then
you have hard disk drives, or HDD. So with the optimized hard drives first, they're
used for frequently accessed data or big data that needs to be filtered. You also
have the option of cold hard drives, which is better for file servers or data you
don't need to access as frequently. Cold hard drives have the lowest cost in the
hard drive space. All right, so let's talk about snapshots and how they're
useful. The biggest benefit of snapshots is that they are the picture of an instance
in an EBS volume at a specific point in time. This is really good for things like
redundancy and backups. That way, if something happens, you don't have to
start back from zero. You get to start wherever your particular backup or
snapshot is. All right, it's demo time. Let's jump into the console and take a look at
what EBS volumes look like and how you can attach them. I'll see you there. And
welcome to the AWS console. In the console today, we'll be looking at EBS
volumes and how to attach them. So our first step is going to be going to the EC2
section of the console. We're going to go up to the search bar, type in EC2. This is
assuming you don't have it on your Recently visited or on your bookmark bar.
Click on EC2. And as you can see, we are at the EC2 home page. So from this
section, you can see that we currently have one instance running. But what we're
looking at today is going to be the Elastic Block Storage. So we're going to click
on Volumes, and this is the volume that's currently attached to the EC2 in
use. You can see that by the In-use section right here. You can also see
what availability zone it's in and what time it was created. Let's go ahead and
create another Elastic Block Storage volume. So how we're going to do that is
we're going to go up to Create volume, and here's where we get to make
some decisions. What type of EBS volume to make. We're going to go ahead and
leave it on General Purpose, gp2. What size we're going to make it. We're going to
change this from 100 to 50, then we're going to change what availability zone it is
to match the EC2 instance that's currently made. Now down here, you can see
that there are tags. Tags are really important when it comes to your EBS
volumes, especially if you're using this interchangeably with other instances. If
you're going to have an EBS volume that has a specific thing on it like an
application or a particular file, it's really important for you to name that EBS
volume so you can always keep track of where that volume is. So I'm going to go
with Name, and we're going to call it Test. So the last thing I want to talk about is
the snapshot ID. These snapshots are images of particular EBS volumes, so you
can create your own EBS volume to work like these. Now these are from other
EC2 instances that have been used on this account. So we're just going to leave
it at blank at the moment. But if you were wanting to create a volume from a
snapshot, like let's say you were trying to do data recovery, you can always do
that from the screen here. So we're going to go ahead and create a volume, and it
might take a second for it to become into use. Okay, and as you can see here, it is
currently available. So we've got our Test volume, this is our volume ID, and then
we've got its available status so that we can attach it to an EC2 instance. So how
we can do that is we go up to Actions, Attach volume, click on the running
instance, and then we could talk about what name we're going to do on the
device, in other words, where we're going to actually place this volume in the file
structure. We'll go ahead and leave it at /dev/sdf for now. In Linux systems, it'll be
this, in Windows systems, it'll give you a letter association. So we're going to go
ahead and Attach volume. And as you can see, as stated here, it is currently in
use. Now let's say that this EBS volume now has the very important data from our
server that it was attached to. And we wanted to take a snapshot of this
volume. What we can do is go into Actions, Create snapshot, and we're going to
call it Mission Crit, in other words, mission critical for this particular thing. Then
we're going to go ahead and click Create snapshot. And if we click on Snapshots,
we have our snapshot here. Now this process can take a distinctively long time if
you have more information or more data on your particular instance. It's also
a good idea to try and create an instance from this snapshot just to make sure
everything is working, then you can easily delete the instance afterwards. But it's
just to make sure that hey, our redundancy is working and our snapshot has
actually worked effectively. So if you click on this little plus here, you can see that
you can copy the snapshot, create an image from that snapshot, and that's how
you can create an EC2 instance from it. Or you can create a volume snapshot like
we did here. So you can create more EBS volumes off of that. You can also set up
your snapshots to have a lifecycle. In other words, you can have them set up to
have a specific snapshot every day at a specific time. Which can be really useful
if you have things like ever-changing data or if you have a database that has
specific data needs, it can be useful in those sorts of situations. And with that, let's
head back to the slides so we can take a look at what we touched on in this
lesson. I'll see you there. And welcome back. Let's go over what we touched on in
this lesson. First, we talked about what an EBS volume is. Then we talked about
what the different volume types are and their best uses. We also talked about
what snapshots are and why you should utilize them. And finally, we jumped into
the console to see EBS volumes in practice. I hope this cleared some things up,
and I look forward to seeing you in the next one.
Creating Security Groups and Why They Are Important
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we'll be
talking about security groups, what they are, why you should definitely use them,
and then we'll jump into the console to take a look at what security groups look
like in practice. Let's get started. Security groups are the main protector of your
EC2 instances. They help with what you can and can't connect to,
blocking access to places and people that you really don't want to see your
resources. They can be a bit tricky to get right, so if you're having connectivity
issues, they're one of the first things that you should check out. But the good
news is that they can be shared across other resources. Things like RDS instances
and lambda functions can use the same security group. So now that we know
what a security group is, let's talk about why you should definitely use them. First
and foremost, obviously is security. With security groups, it's really important to
keep your environment safe and allow your resources to see each other. It's also
helpful for your environment to keep organized and to see what association of
what goes with what. All right, it's demo time. Let's take a look at security groups
in the console. I'll see you there. Welcome to the AWS console. In today's demo,
we're going to be taking a look at security groups and how to add a security rule
into a group so that you can easily connect from one instance to another. So from
the home page, how we're going to get to the security group section of
the console is we need to jump to the EC2 section first. If you don't have it in your
Recently visited, you can go up to the search bar, type in EC2, click on EC2, and
click on Instances (running). So right now I have two instances currently in the
Running state. I have this Bastion instance, which has a public IP, and this private
instance that has only a private IP. What's also important to note is that these
two instances are in the same security group, which is important for how you set
up your rules. So in order for you to be able to connect from this Bastion into this
Private instance, we need to make sure that our security group allows access for
it. So what I'm going to do is copy the public IP address here. There are two ways
to find the security groups. You can either find them under Network & Security on
the side bar here, or you can click on Security groups here and open the security
group. So currently, there is only one security role in the security group, and it is
the allowing of SSH from my IP address. With security groups, you can always
specify an allow rule, but not a deny rule, which is why it's really important for you
to add rules to make sure that you can connect properly. So what we're going to
do is we're going to edit the inbound rules, so click on that, and we're going to
add a new rule. So from here, we can change what type of rule we're going to
add. If we wanted to make sure that our website was visible, we could click the
HTTP, which allows anyone to view our port 80 registry. If we're wanting to do
HTTPS or a secure version of HTTP, that opens port 443. But as you can see, there
are a lot of different options when it comes to the security groups, which is really
important when you're trying to do your normal everyday business. In this
particular case, we're going to click on SSH, and we're going to click on
Custom. We'll go ahead and paste the Bastion IP here to our security group. Click
Save rules. And there we have it. We've added a security rule to our security
group under our EC2s. The Bastion instance can now connect into the private
instance using only the private IP address since they're both in the same
network. Let's head back to the slides so we can review what we learned in this
particular lesson. I'll see you there. And welcome back. Let's go over what we
touched on in this lesson. First, we talked about what a security group is, then
we talked about why you should use them. After that, we jumped into the console
to take a look at security groups in practice. I hope this cleared some things up,
and I look forward to seeing you in the next one.
What Is Auto Scaling and How Does It Work?
Hello, everybody. Welcome back to AWS Essentials. In this lesson, we're going to
be going over auto scaling, what it is, and how you would use it. Let's get
started. So, let's talk about Auto Scaling groups. What are they? An Auto Scaling
group allows you to have a dynamic environment. That means that you can scale
out, depending on the activity in your environment. So if you're getting a lot of
traffic on an EC2 instance, if that EC2 instance is part of an Auto Scaling group, it
can automatically add another EC2 instance to help lighten the load a little
bit. Auto Scaling groups also let you curb costs as you only really have what you
need inside your environment. So now that we have a better understanding of
what Auto Scaling groups are, what are some of the reasons that you might use
them? Realistically, there are two main reasons, efficiency and the overall health
of your account. With efficiency, you have automation integration, creating
policies for when your system scales out like at a specific time when you know
you'll be busiest or if things like an EC2 instance hits a certain TPU utilization. It
can scale out the number of instances that you have, so that way it can always
dumb that down just a little bit. And with health, you always have constant health
checks going with your Auto Scaling groups. So that means if an EC2 instance
isn't inside the health range that we need it to be, it can be terminated and a new
one put in its place. All right, it's demo time. Let's jump into the console and take
a look at Auto Scaling groups in practice. I'll see you there. And welcome back to
the AWS console. So in this trip into the console, we're going to be talking about
auto scaling and how it works. But in order to talk about that, we need to go to
the EC2 section of the console. If you don't have it here on your Recently visited
or in your bookmark bar, we can go up to the search bar and type in EC2, hit
Enter, and we see we have some instances running. It looks like we've got
currently two running instances, but three instances overall. But the thing we're
actually going to look at is we're going to go down to Auto Scaling, and we're
going to go down to Launch Configurations. So we're going to create a launch
configuration. And from here, we're going to create a launch template. So in this
template, we are going to say, hey, this is going to be our Webserver. We're going
to say it's a Prod Webserver. All right, and since we don't have any AMIs
currently, we can also pick one of the AMIs that we're currently using. For
example, since we have some instances already running, we could pick one of
these particular instances and use that as our section here. So since we already
have an AMI for a Linux instance already ready, we're going to click on that. We're
going to include an example for the key pair, and we're not going to pick which
subnet it's supposed to go into. We're going to select an existing security
group. We're going to click launch-wizard-1, then we're going to click Create
launch template. Now we're going to view our launch template. So here is our
launch template. This is where we can modify it or launch instances from this
template and go from there. If we were going to modify it, it would go back to that
same screen that we had before. So we're just going to Cancel here, and then
we're going to go back to Auto Scaling. We're going to click on Auto Scaling
Groups, Create Auto Scaling Group. We're going to click on our Webserver
template here. And this Auto Scaling group is going to be Webserver. So we're
going to use the default version. It's usually recommended that you use either
the latest version or the default. Either of those options are the best option for
you. Hit Next. And here's where we get into the thick of it. So now we get to
select which subnets we want instances to go into. I'm going to go ahead and
click all six here. So here are the instance type requirements. We're not going to
have a minimum. We're also not going to have a maximum. Same thing with our
RAM here. We are going to pick a t1.micro. Now here's where we get our
purchasing options. If what we were doing for our Auto Scaling group
wasn't completely necessary or we had extra options here, when it comes to our
latency, we could always change what type of on-demand versus spot instances
that we have. As I explained in a previous lesson, spot instances are an instance
where you can actually pay a specific amount, and it goes over that amount, then
your instance turns off. On-demand is a little bit more expensive, but you don't
have to worry about it turning itself off on you. So we're going to click on the
lowest price. Hit Next. We're going to create a new load balancer. It's going to be
an Application Load Balancer. We're going to do target group as Webserver, and
health checks are going to be on the EC2 and on the ELB. So we're going to hit
Next. So here's where we get our desired capacity. As you can see, there are
different options for what our desired capacity is. You can either have it as for
your CPUs or how much RAM you're using, or you can have specific units, in other
words, specific instances and how many there are there. So we're going to put a
Desired capacity of 2, a Minimum capacity of 1, and a Maximum capacity of 4. So
we're not going to change any scaling policies at the moment, and then we're
going to hit Next. Here's where you could add a notification. So that way if ever a
scaling action happens, either a new instance gets launched or an instance gets
terminated, you would receive a notification for that. We're going to go ahead
and skip that and hit Next, and then we'll hit Next again. And here is the Review
section. So this is just all the sections that we talked about before. So we're going
to click Create Auto Scaling Group, and this can take a second. All right, we
currently have a Webserver scaling group, and we're updating the capacity
because we had said we want a Desired capacity of 2, and we currently had 1. So,
if we click on EC2, we click on running instances, and then we get rid of the
running sorter there. And here are our instances for this particular Auto Scaling
group as it's getting installed into our section here. Let's head back to the slides
to take a look at what we covered in this lesson. I'll see you there. And welcome
back. Let's go over what we touched on in this lesson. First, we talked about Auto
Scaling groups, what they are, and how they work in theory. And then we jumped
into the console to see how they work in practice. I hope this clears some things
up, and I look forward to seeing you in the next one.
Associating IP Addressing
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we'll be
covering IP addresses, what they are, what private versus public IP addresses
look like, and then we'll take a jump into the console to look at what IP addresses
look like in practice. Let's get started. IP addresses stands for Internet Protocol
address, which allows for the communication between networks. Think kind of like
a home address. Your IP address is the identifier for your resources in both your
VPC and in the internet as a whole. So let's talk public versus private. Your public
IP address, like the name implies, is publicly accessible. It means you can access
it from just about anywhere, but it's also not as secure as a private IP
address, meaning that it can potentially have attacks and all sorts of nasty stuff
happening to it. Whereas a private IP address is much more secure, but it does
mean that it's only accessible inside of that network. All right, it's demo time. In
this demo, we're going to be talking about how to access a private instance
through a bastion host. In the real world, we'll be using the bastion host to access
these private instances to keep our private instances safe. I'll see you there. And
welcome to the AWS console. In today's demo, we're going to be talking about
how to associate IP addresses with EC2 instances. So in order to do that, we need
to get to the EC2 section of the console. If you don't have it in your Recently
visited section, go ahead and head up to the search bar, type in EC2, click on
EC2, and we're going to launch a new instance. So where it says Launch instance,
we're going to click on that. So we're going to call this the Bastion server. We
want it be the t2.micro, our example key there. And now we're going to edit some
network settings. We're going to change from the default VPC to the project
VPC. We're going to go ahead and go into the public subnet, and we're going to
auto assign a public IP address. So we're going to collect an existing security
group. And with that, we're going to click Launch instance. All right, let's click on
that instance. And it takes just a second to finish out, so I'll be right back once it's
finished. Okay, and as you can see, it is currently in the Running state. If we go
ahead and click on this little checkbox here, we can see that it has a public IPv4
address. This is a way for us to easily connect into an instance. It also has an IPv4
private address, which is inaccessible outside of the network. Now the other
thing that I'm going to show you is if we go ahead and copy the subnet ID, click
escape there, filter it by that subnet ID, that there is a Private instance, as well as
our Bastion instance. Now the reason I have it currently set up this way is so that
you would have to log in into this Bastion instance to this IP address here. And
then once you're in this particular instance, you can use the private IP address to
get into this instance here. You'd have to log into the public instance first before
you can log into the private as you have to be inside the network before you can
use a private IP. I hope this cleared some things up. We'll go over logging into the
instances in another video. Let's head back to the slides so we can take a look at
what we learned in this lesson. I'll see you there. And welcome back. Let's go over
what we touched on in this lesson. First, we talked about what an IP address
is. Then we talked about private versus public in the IP address context. Then we
jumped into the console to take a look at IP addresses in practice. I hope this
cleared some things up, and I look forward to seeing you in the next one.
Defining Resource Groups and Tagging
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about resource groups and tagging, specifically what they are and
how to utilize them. Let's get started. Okay, so first things first, resource
groups. What exactly are they? Resource groups are a collection of instances
that are put together for a variety of reasons. It could be they're on the same
project or they need to be on the same patching schedule or even something as
simple as they were made at the same time. But realistically speaking, you have
three reasons why you would use a resource group, for organizational
purposes, security purposes or just straight up efficiency purposes. When it
comes to organization, it allows you to group your instances specifically
together, things like allowing specific teams or specific projects to have control
over those particular instances. With security, it adds a specific layer of
protection because you're notating which particular instances need specific
things, things like a deletion date for an instance or even what group is working
on what specific thing. When it comes to efficiency, resource groups come in
handy for things like easy patching or filtering when you're using specific types of
automation. And resource groups realistically go off of one thing, tagging. So
resource tagging allows you to add information about that resource to an outside
observer. So inside the console, when you add a tag to your particular instance, it
allows you to add more information and more context about what that instance is
besides just having a specific name for an instance, things like projects or what
person built it or if it's related to a specific stack with automation tools. So, now
that you get the gist of what exactly is going on with what a resource group and
tagging specifically goes with, let's go take a look at the console and see how
they work in practice. I'll see you there. Okay, everybody. Here is the AWS
console. So from this console, we're going to take a look at what instance tagging
and resource groups actually look like. We're going to be using EC2 as an
example today. But realistically, you could also use this with RDS. So for resource
groups in tagging, because we're going to be using EC2 as an example, we're
going to head over to the EC2 section of the console. So we're going to go up to
the search bar, type in EC2, then click on EC2. So as you can see, it says I
currently have three instances running, so I'm going to go ahead and click on
Instances. And there you see, I have three test instances currently active at the
moment. So, let's take a look at one of these instances. In order to see the
tags, we're going to click on this little checkbox here and go over to Tags. So as
you can see, it already has a singular tag, which is the Key of Name with the Value
of Test. So that's why you see in this Name section, it says test for all three of
these. So, all three of them have the same tag. But how would you go about
manually adding a tag to this particular instance? Well, from this particular page,
we would go to Manage tags and then Add new tag. So, let's say this particular
instance was used for a new website project. In order to add that tag to this
particular instance, we would type in Project, and for the Value, we would type in
Website, and then we'd hit Save. So once it saves, when we click on that same
instance again, we can click on Tags and see that it's saying Project Website. So
let's say for this example though that you had about 10 to 15 instances that you
had to add to this particular website project, and you really don't want to go
through and manually add all of them. From the EC2 console, there is a way to
add tags to multiple instances. So from this page, we're going to go over to
Tags. And as you can see, there it's showing a list of what exactly our tags are
listed. So take, for example, we have the Name tag, which has the value of test,
has a total of 3 instances. But the Project tag with the value of Website only has
1. But we want those other two test servers to also have the Website tag. What we
would do is we go to Manage Tags. And since we know this first instance is the
one with the Website tag, we would click these two boxes, go to where it says
Key, click on Project. And under Value, we'd click on Website and then Add
Tag. And see? Now all three instances have that Website tag, and this can be
done with new tags as well. So let's say that all three of these instances
were being handled by the IT department. We would type in Department and
with the Value of IT and hit Add Tag. This can also potentially remove tags. So
let's say that the IT department was no longer looking after this website. In order
to remove tags, we would just put Department here from that little drop-
down menu and hit Remove Tag, and there you go. The tag has been removed,
and they're no longer the IT team's problem. But let's say that you were trying to
find some instances that you weren't sure how they were tagged. There's a way
to find that as well. We can go back up to the search bar. We go to Tagging, and
that'll pop up with Resource Groups & Tag Editor. We're going to go ahead and
click that, which will take us to the resource group landing page, but we're going
to go to the Tag Editor first. So, over here on the left, we're going to click on Tag
Editor. So all of our resources were built in us-east-1, and we're going to click on
Resource types, EC2, click on EC2::Instance, and then click Search resources.
And there is all of our instances. You can see that it tags with the specific name,
as well as the total of tags that you currently have on that particular
instance. There's even a way to add tags from this particular screen. How I would
do that would be we click on this little box here, click on Manage tags of selected
resources, then we click Add tag. So, let's say that we were going to set up these
particular instances so that they were running our website, but we need to notate
which instances are running Windows and which instances are running Linux. In
this particular case, all three of these instances are running Linux. But how we
can notate that so somebody doesn't have to go through the instance summary
page to actually try and find what operating system these instances are on, we
can create a tag that specifies the OS level. So, we would type in OS with the tag
value of Linux. Click on Review and apply tag, Apply changes, and then Search
resources one more time. As you can see, our instances pop back up, and they
have three tags now instead of two. But let's say you wanted to make a resource
group, specifically so you can make patching once a month a little bit easier. How
would we do that? Well, we'd go up here to where it says Create Resource
Group. Click on that, and this is where we can create a resource group or create a
grouping of our instances. You have two options when it comes to resource
groups. You can do a tag-based resource group, in other words, you're sorting
your instances by a specific tag that is on those instances, or you can do a
CloudFormation stack-based resource group. Now CloudFormation is an
automation tool that allows you to build out resources in a more efficient way. And
don't worry, we'll be covering that a little bit later in this course. In this particular
instance, we're going to be looking at the tag-based resource group. So we're
going to keep that on Tag based. And then for Resource types, we're going to
type in EC2. Click on Instance. Now if you click on Tag key, you'll see that there's
a number of things that pop up. These are the potential tag options that you can
use for your resource group. In our particular case, since we're using this as a
group for what instances are going to get patched when, we're going to click on
the OS tag. And specifically, we're going to add the Linux tag to this resource
group. So to make sure that we have all the instances that we want inside of this
resource group, we're going to click on Preview group resources. And there it
goes, we see all three of the instances that we wanted in this particular resource
group, all three tags are listed, and these three things will be in a group
together. So for the Group name, we'll go ahead and call this Linux so that way
we can have an actual Linux patch group, as well as a Windows patch group at
some point. So from there, we're going to hit Create group. And there we have
it. So we see that the Group name is Linux. It is a tag-based group, specifically for
AWS EC2 instances, and the tag is OS: Linux, using these three resources that are
there. You can always see your saved resource group by going under here
and clicking Saved Resource Groups. And that'll show you what specific resource
groups are available to you. Let's go back and do a quick review on what we
touched on in this lesson. So it's time for a quick review. What exactly did we go
over in this particular lesson? The first thing we covered, which was what exactly
are resource groups? Then we talked about instance tags, and then finally, we
went into the console to take a look at how resource groups and instance tags
work together and how you would put them onto your instances. I hope this
cleared some things up, and I look forward to seeing you in the next one.
Understanding Elastic Load Balancer Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about Elastic Load Balancers, what they are, how they work, and
then we'll jump into the console to see them work in practice. Let's get started. So
ELB is an acronym that you'll see thrown around quite a lot in the cloud space,
and it stands for Elastic Load Balancer. Elastic Load Balancers are around to help
you get your traffic to an endpoint, be that endpoint a website or an application.
ELBs also have an extremely good health check system to make sure that all of
their target groups, the instances that you're pointing your traffic to, are always in
a healthy range. So now that we have an overarching idea of what a load
balancer is, let's talk about the two different ELBs that are in AWS. First, we have
the Application Load Balancer. They're incredibly versatile and customizable with
a lot of different options on where you can send your traffic to go. And then we
have Network Load Balancers. They're a little bit simpler, were they directing
traffic on or not style of running. But because of that, they can handle a lot more
heavy of a load. So let's jump into the weeds a little bit when we talk about
these two. Let's talk about the top three things about both these particular types
of load balancers. First, Application Load Balancers. Normally, Application
Load Balancers are going to be your internet-facing public subnets. Application
ELBs are also context-aware, meaning they can understand if you're looking
for something specific to an application or to a website and will direct your traffic
accordingly. There are also a lot of customizable variables when it comes
to application ELBs, which allow you to have more control over who goes where
and does what. Then we have network ELBs. Normally, they're held within private
subnets, so they're not necessarily internet-facing. They also don't have context,
so they'll direct traffic wherever you point them. But because of that, they can
handle quite a bit more traffic than your average Application Load Balancer. All
right, it's demo time. Let's jump into the console and see what they look like in
practice. I'll see you there. And welcome back to the AWS console. So from the
console today, we're going to be looking at ELBs and how they work. So in order
to get to the ELB section of the console, we're going to need to go to the EC2
section of the console. If you don't have it on your Recently visited or you don't
have it on the search bar up here, what you can do is go into Search, type in
EC2, click on EC2, and here we are at the EC2 home page. Now as you can see, I
currently have two instances running. We'll need those for our target group and
load balancer later. But speaking of that, let's go ahead and go make a target
group for our load balancer. So we're going to scroll down to where it says Load
Balancing, click on Target Groups, and it says we currently have no target groups
in us-east-1. Let's change that. We're going to click on Create target group. So
here's where it can get a little bit into the weeds. Your target group can be just
about anything. It can be a specific load balancer. It can be instances that are
inside of your VPC. If you have something that's on-premises and are load
balancing to it, you can do it off of IP addresses. Or if you have a lambda function
that's working as your application, you can also set that to be part of your target
group. In this particular case, we're going to stick with instances. We're going to
call this Target group Websites. We're going to keep the HTTP protocol, which
means it has to be open on port 80. I'll keep it on HTTP1 for now and leave the
health checks on HTTP. Now we're going to click Next. All right, and we're going
to click on both of these instances. We will go ahead and click Include as pending
below, then we'll Create target group. And now we've got our target group
created. With our target group created, now we can go ahead and actually create
our load balancer. So let's click on Load Balancers, and then we're going to click
Create Load Balancer. So from here, we're going to click on the Application Load
Balancer. So we're going to click Create. Load balancer name is going to be
Website. We're going to have it be internet-facing since we want it to be
directing traffic to our website. It's going to have IPv4 IP addresses. And
the mappings for these are going to be in us-east-1a. We're going to keep the
default security group, though you can select more if you want to like the launch
wizard we used for making the EC2s. And this is where the listener comes into
play. We can either have it as HTTP or HTTPS, which means it'll be on port 80 or
port 443 respectively. In the Default action, when traffic comes in on this port 80,
we're going to forward it to the website's target group that we made, in other
words, those two instances. We're going to go ahead and leave tags and the
acceleration alone. But here is our summary of the Elastic Load Balancer we're
going to create. It's going to be internet-facing and IPv4. It's going to have the
default security group. It's in our default VPC and subnet pointed at our Websites
target group. So let's go ahead and create our load balancer, and then we're
going to click View load balancer. So its current State is Provisioning, and we'll
come back in just a minute when it's actually finished. Okay, and we've got our
active ELB. As you can see here, it says its State is currently Active, and we can
see the DNS name that we would add into our Route 53 port right here. We also
have it here. It even tells you what type of record you need to make it. It's going
to be an A Record. Don't worry, we'll be going over Route 53 and what those
records mean a little bit later. So let's jump back to target groups really quick. So
let's click on the Websites target group. And as you can see here, we currently
have two unhealthy hosts. Now this was an in-production environment. This right
here would be a problem because that means that nothing can actually get into
your ELB. That means even if your ELB is directing traffic to your instances, it is
not allowing your traffic to actually flow through them. In the management tools
section, we'll talk about CloudWatch and how to make alarms so that if something
like this happens, you can be informed about it. Let's go ahead and click on
Monitoring. As you can see here, it's saying we have two unhealthy hosts
because they aren't able to reach that particular section. When both the hosts
are healthy, they'll move over into this little green section here, and you'll be able
to send information through the ELB to the actual devices. Let's head back to the
slides to take a look at what we learned in this lesson. I'll see you there. And
welcome back. It's time for a quick review on what we touched on in this
lesson. First, we talked about what an ELB is. Then we touched on what you
might use it for. After that, we jumped into the console to see how they work in
practice. I hope this cleared some things up, and I look forward to seeing you in
the next one.
How to Create and Utilize an EC2 Instance
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over how to create an EC2 instance, both in theory and then jumping
into the AWS console to spin one up in practice. So, how do you make an EC2
instance? The first step is logging into the AWS console, then navigating to the
EC2 section of the console, and finally, using the EC2 wizard to launch an EC2
instance. All right, it's demo time. Let's jump into the AWS console and take a look
at how to launch an EC2 instance in practice. I'll see you there. And welcome to
the AWS console. So, in this console, we're going to be going to the EC2 section
of the console, going to the running instances, and then creating a new
instance. Now, if you haven't recently been to the EC2 section of the console and
it's not here, how you can get to the EC2 section is go up to the search bar, click
inside, type in EC2. It should pop up right there, then we click. Okay, and it says
we've got zero running instances. So there are two ways that you can create a
new instance. The first way is to click this Launch instance button, which if you
already have a preset template for how you want your instances to be, that would
pop up right here. Since I don't have one of those right now, we can just click the
Launch instance button. The other way to do it would be to click on your
instances running, and then you can click the Launch instance button from
here. So go ahead and click Launch instance, and here is going to be the EC2
launch instance wizard. So with this particular wizard, it is going to help you to
build out your EC2 instance. As you see over here, it's going to tell you how many
instances you're building. If you're wanting to build more than one, you can build
two. It also tells you things like consider an Auto Scaling group if you're building
out more than one. We'll cover Auto Scaling groups in another lesson. But you'll
also see it says the instance type, what AMI you're using, if there's going to be a
security group attached to it, as well as what your volume of storage is. All of
these are editable options that you can potentially change inside of the wizard. So
first things first, we're going to name it. We're going to name it Test. We're going
to go ahead and keep Amazon Linux. It's an Amazon Linux 2, which is one of the
more recent kernels. We're going to go ahead and keep it on t2.micro as it's
eligible for the free tier, which is always nice. So here's the Key pair section. So
your key pair is how you're going to log into your instance. Now, I already have a
key pair. But if you don't have a key pair, all you do is click on this Create new key
pair button, name your key pair, and then download it into your computer so you
could use it to access your instance. Since I've already got one, I'll just go ahead
and use Example. It's going to go into the default VPC. Since I don't particularly
have a preference for subnets, we're also going to go into defaults there as well.
So here is where it gets into security, and this is important. So when you're
creating a new instance, you can either do an existing security group if you have
one already, or you can create a new security group with what you're doing. So
you can allow SSH traffic from anywhere, or you can do it specifically from your
IP. Or if you're looking to have somebody go from a specific IP, you can hit the
Custom button and then type your IP address there. If you're going to have a
website present on this particular instance, you can click Allow HTTP and HTTPS,
which allows traffic in on port 80 and port 443. We'll go ahead and click both of
those boxes. So, as you can see, it currently has one volume at 8 GB, and it's
a gp2, which should be just fine for our purposes. There's also the section for
Advanced details if you're looking to do things like adding it to a domain if
you're using a Windows-style instance, or if you have a specific IAM profile of how
you're going to use this instance, you can add that here. Or if you're looking to
change it instead of an on-demand instance, you want to request a spot instance,
you can click that here. But there are a lot of different options when it comes
to the advanced section of the console. Auto-recovery. You can change your
shutdown behavior. If the instance is shut down, it stops it completely, or it will
straight up terminate it. You can also click on Termination protection to make
sure that the instance can't be deleted without somebody specifically deleting it
in your console. You can also do the same thing with Stop protection to make sure
your instance doesn't get stopped. Detailed CloudWatching. There are a lot of
different options here, which can really get you into the weeds if you're not
careful. But they can be incredibly useful if you're trying to build out
your template or have a specific need for your instance. They also have a section
specifically for User data where you can bootstrap certain information. And when
I say bootstrap, I mean that you can add specific code in to allow your instance to
start up with a particular application already installed in the instance. I'm not
going to go ahead and add that at the moment. Whenever you've picked
everything that you want, you just go ahead and click this Launch instance
button, and there we go. We have successfully launched this instance. You can
either click on the instance link here, or you can click on the View all instances
button. Either of these options will get you to where you need to be. I'll go ahead
and just click on the instance ID, and it takes us here. So as you can see, the
instance state is currently Pending. It can take a minute for it to actually start
up. I'll be right back once it's actually done, and we're in the Running state. So if
we click on this little checkbox here, we can see all of the details that we selected
when we were going through the launch phase. You can see that it's added a
public IP since we've opened up certain ports. We can also see what type of
platform it is. It is Amazon Linux. It is a Linux or UNIX platform. It doesn't have stop
protection, and this is the key pair. Let's head back to the slides to take a look at
what we learned in this lesson. And we're back. Well, let's go over what we
touched on in this lesson. First, we talked about how to create an EC2 instance in
theory, then we jumped into the console to talk about how to launch an
EC2 instance in practice. I hope this clears some things up, and I look forward to
seeing you in the next lesson.
How to Connect to an EC2 Instance
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over how to access EC2 instances, both through the console and
through your computer. Let's get started. So, how would you connect to an EC2
instance from AWS or from your personal computer? The first step would be
logging into the AWS console. The second is going into the EC2 section of the
console and then retrieving the IP address for the instance that you're trying to
connect to. And then finally, you would log into the instance using a third-
party software like PuTTY or an RDP manager. There is also an option to log into
the AWS instances through the console itself if your security settings are set up
correctly. All right, it's demo time. Let's take a look at all the ways you can log into
an EC2 instance. I'll see you there. Okay, and welcome to the AWS console. So in
order for us to get the information that we need in order to log in to these
instances, we're going to need to get to the EC2 section of the console. How we
can get there, if you don't have this particular button here that says Recently
visited or this button here on the task bar that says EC2, you can find it really
easily by going up to the search bar, typing in EC2, click on EC2, and it'll bring
you to the EC2 console page. So from here, we're going to click on Instances. And
the first thing I'm going to do is show you how to get into a Linux box for my Linux
or Mac computer is you'll need a Linux instance. This one I have is prebuilt
here. And as you can see, it has a couple of interesting features about it. The first
and foremost being that I have added the SSMRole to it to make sure that it's
accessible from a couple of different locations. But realistically, all you actually
need to access your instance is going to be this key pair right here. I have already
downloaded this key pair. It's something that you get and create when you
actually make your instances, which I've covered in another video. So let's talk
about how we're going to connect to this particular instance. You have a couple
of options. The first and foremost, we're going to need the public IP address for
this particular instance. So if you click on these two boxes here, it's going to copy
that particular public IP address. But do you remember that thing where I was
talking about, the adding the SSMRole to this particular instance? Adding that
role to this instance means that when we click the Connect button here, we have
the option of opening Session Manager to take a look at this instance that
way, allowing us to have a terminal inside of our browser window itself. Generally
speaking, this usually isn't something I would recommend for most people as it
can potentially cause complications if you're using your instances certain
ways, but it can be really useful for quick edits and things like that. In order to
leave this particular window, you would just click the Terminate button, then
terminate your session, and we can go from there. So if we're going to connect
with an SSH client, here's some of the stuff that needs to happen. The first thing
is you need the instance ID, and we'll need to update our key that we got when
we built out this instance to something else. But since we've got that information
already, let's go ahead and head to the terminal to take a look at how we're going
to access this device. Okay, so how we can get there is we click on this Terminal
button here, and that brings us into our terminal here. So from the terminal, what
we can do is go into our downloads. So we type in cd, capital Dow, hit your tab
button, and that's Downloads. Hit Enter or Return. And as you can see, we're in
our Downloads folder now. So from our Downloads section, we're going to have to
change what our security is for that particular PEM key that we downloaded for
this instance. How we're going to do that is we type in chmod 400, meaning that
the file is readable and accessible, but not executable, and then whatever your
key is. In my case, I put it as Test.pem. Hit Enter, and there we go. We now have
our test key PEM as the correct outline for us. So, in order for us to log into our
device from the terminal, like we're doing here, how we would do that is we type
in ssh -i. Now, if you're wanting to SSH from somewhere else inside of your
terminal, like your home directory, you'll just have to write your file path here for
wherever your PEM key is. Since we're doing it in the same file as that particular
PEM key, I'm just going to write Test.pem, and then we're going to do ec2-user at
the IP address that we had from earlier. Hit Enter. Okay, when this pops up, it's
saying, hey, you haven't accessed this device before. Would you like to continue
and connect to it? We're going to type in yes. Hit Enter, and there we have it. We
are now logged in to that EC2 instance from our Mac or Linux computer. And
from here, you can do all the same commands like you would normally do in a
Mac or Linux environment. So, let's talk about how to get to a Linux box from a
Windows machine. Okay, so from a Windows box, in order for us to go from
Windows to Linux, there is just a few extra steps we need to take. So as you can
see here, I have my Test.pem key here, as well as this PuTTY application
here, which is how we're going to log into our instance. But you'll also notice I
have something else here. It's called PuTTYgen. So in order for a Windows
machine to log into a Linux box, one that specifically uses a PEM key, you need to
change that PEM key from specifically a PEM to a PEP key that PuTTY can
understand. When you go to download PuTTY, there will also be an option for you
to download PuTTYgen, which generates this PEP key. So if we click on
PuTTYgen, you can see that there currently are no keys in this particular
generator. Now looking down at Actions, you see that there are a couple of
different options here. There's the option to generate a public key or a private key
pair. There's also the option to load an existing key pair, or there's an option to
save them. Since we don't have anything right now, the saved options are
blacked out. So we're going to click Load since we already have a key that we
want to generate. So from the desktop, we're going to change the output from
PuTTY keys to All Files and click on the Test.pem here. Then click Open. This is
saying, hey, just so you know, you're putting in a different type of key. Just hit
OK. And since we see that it has actually imported our key here, we can go ahead
and save this private key. Now if you were doing this on your own instance, I
personally would recommend doing a passphrase. That way, you can make sure
that you have that double layer of protection just in case. Since I don't
necessarily need that for this example, I'm just going to go ahead and click
Save, then hit Yes. And I'm going to type in Converted-test and then hit
Save. Okay, so we have successfully generated a key for our Windows instance. So
we're going to hit X, and now we're going to open PuTTY. So from PuTTY, we are
going to go to a couple of different options first, the first being that hostname
that we're going to use for this particular instance. We're going to take that public
IP address. Okay, so we have our IP address put in, and now we're going to go
down to Data. This is where we're going to put in what login we're going to use for
this particular instance. And just like with the terminal instance, we're going to
type in ec2-user. And then the final piece of information that we need is under
this SSH section. We're going to click this little plus here and then click where it
says Auth. So from this authorization section, we're going to open that converted
key that we just made. So we're going to click Browse, Converted, Open. All right,
so with all three of those pieces of data in, we can click the Open button, and
that should save our instance. However, if you're wanting to log into this instance
a lot or you'll be making quite a few changes to this device, you can always save
these sessions under a specific name. So let's say it is maintenance. You'd click
Save. And that way, you can easily open a session without having to add extra
bits to it. So we're going to hit Open, and there you have it. We are back in that
particular instance again, but this time from a Windows device. Now, if you're
wanting to quickly get into this device, say you saved that session information, all
you would have to do after that is click on PuTTY, load your maintenance section,
hit Open, and there you go. No having to input extra data, just a simple two-
button switch. So now that we've gone over how to get into a Linux box, let's talk
about how to get into a Windows one. We're going to go into the Start menu
here. We're going to type in rdp, Remote Desktop Connection. Now from here, this
is going to be how we're going to connect into a Remote Desktop session from
our system here. What we need is that computer information. So from EC2, we
look at our instances, click on Connect and RDP client. Then we copy the public
domain information and paste that here, hit Connect, and then it's going to ask
for a username and password. We can get that once again from the console. So
the username is going to be Administrator. So we just type that in here, and then
we go back to the console to get the password. So as you can see here, you see
this Password button. We're going to select Get password, and here, it's going to
ask for the key pair for your particular instance. All you have to do is click Browse
wherever you have your particular key pair. I'm going to click on my key pair
there. You see this green little check mark indicating that it's the right key. Hit
Decrypt password, and you can see that it is currently offering us that
password. So we're going to copy that particular password and then paste it back
in this box, and then hit OK. This section will pop up saying, hey, we're not sure
about the certificate for this device. Just hit Yes. This can take a second for it to
actually log in for the first time as it needs to set up your personalized settings
and all that good stuff. And there we have it. We have successfully logged in to
an EC2 instance from a Windows device using your RDP settings. So, now that
we've gotten in from a Windows device, let's talk about how you get into a
Windows box from a Mac computer. There are a couple of different options to get
to a Windows device from a Mac computer. In this particular case, my normal
recommendation would be to go into the App Store and get the Microsoft
Remote Desktop function. It is available on Mac computers, and there's a pretty
easy way for you to get into it. All we'd have to do is go into Add PC. We'll need
the DNS settings that we can get inside of the console. We're going to add the
public DNS record there, and then it's going to ask what user account you would
like to use. We're going to hit Administrator, and then we're going to click Add and
then click on this little box. So from that box, it's going to say, hey, to get into the
Administrator account, we need a password. I always like to Show password
there. We're going to go back into the EC2 menu. Just like before, you'd copy and
decrypt the password, copy the password, then go back to Remote
Desktop, paste password in, hit Continue. And this is just saying, hey, you're
connecting into a Remote Desktop host, do you want to continue? Hit
Continue. And there we go. This is how you would access a Windows EC2 from a
Mac or Linux device. There are options for you to do this from a Linux device as
well. It's just a matter of generally speaking, you have to have something that can
RDP into the device. With all this said and done, let's head back to the slides so
we can take a look at what we covered today. Welcome back, everybody. Let's go
over what we touched on in this lesson. First, we talked about the elements that
you would need to log into an EC2 instance in theory. And then we looked into
how to log into them in practice. I hope this cleared some things up, and I look
forward to seeing you in the next one.
How to Install Software on Your EC2 Instance
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be covering how to install software on your EC2 instances, both in theory and
in practice. Let's get started. Now when you're installing software on an EC2
instance, the first thing you would need to do is log into that EC2 instance. The
second thing that you need to do is figure out what software you need as there's
a lot of different ones to choose from. And then finally, it's actually installing the
software that you've decided you need. Okay, so let's look at what installing
software looks like in practice. I'll see you there. In the console today, we're going
to be getting into how to install software onto your EC2 instances. The reason
that we're starting into the console today is because we need to get the IP
addresses for our EC2 instances. So if you don't have EC2 here on your recently
visited or on your bookmark bar, the easiest way to find it is go up to the
search bar, type in EC2, and hit Enter. Okay, so we're going to click on Instances
(running), then we're going to click on this t2.micro instance here, and then we're
going to click on this Connect button. So this is going to be our Windows
instance. So how we can connect to that is we're going to download our remote
desktop file here, and then we will connect to it just like I showed you in the
previous video. The other information that we're going to need for this
particular project is going to be the command to get into the Linux instance.
I have shown how to get in with the IP address, but here's how you get in with the
hostname. And click on this guy right here to copy the command that we need
in order to log in. And with that done, I'll see you in the terminal so I can show you
how exactly to log in and install software. Okay, so now that we've logged into our
EC2 instance, let's go ahead and get to installing some software. In order to
install software, we're going to need two things. First, we're going to need to do
sudo -i, which will get us into the root user for this particular instance. And then
we're going to type in yum. Yum is a repository that specifically has all the
software that you could potentially need for your instance. So typing in yum
install will install whatever software you put after this. Since these are web
servers, we're going to try and install some web server software on this instance,
this Linux instance here, as well as on the Windows instance that we saw earlier.
On the Linux instance, we're going to install httpd, or Apache. Just so you're
aware, Apache is kind of considered the default for most of the industry right
now. If you're looking at particular web servers, though there are other options
available, things like NGINX and WordPress, the WordPress utilizes Apache as
well. So we're going to type in install httpd, hit Enter. And as you can see, it's
going to install Apache. It's going to install the Apache file system, some tools, as
well as some other applications that are necessary. So we're going to hit yes, type
in y, and hit Enter. And as you can see, we have successfully installed Apache.
How we can test that is go httpd -t. -T is going to be your syntax checker, which
is your best friend when you're doing code first, specifically for Apache. But you
can also find out by typing in systemctl status httpd. As you can see, it's currently
loaded, but it's not active. So we're going to go with systemctl start httpd, Enter. If
we hit the up button twice, we can hit status again. And as you can see, now it
says it's active and running. Now if you want to make sure that your Apache was
able to run all the time, even if your instance just got restarted, let's go ahead and
enable the software to make sure that it can come up even when the instance
goes down and comes back up. So how we do that is we type in systemctl enable
httpd. As you can see, it's added a link here. So that way whenever your instant
starts, it's going to start Apache as well. So with that out of the way, let's jump
over to Windows to see about how to install IIS from there. I'll see you there. Okay,
and welcome to a Windows EC2 instance. So from here, we're going to install IIS
onto this instance. So we're going to go to Microsoft Edge. Now I'm going to jump
to the IIS website where we'll be downloading the information. All right, and we're
going to click on the Web Platform Installer. So we're going to install this
extension, open up the file, and here is the install for this. Here is the licensing
terms and conditions. We're going to go ahead and click I accept and Install. All
right, then we click Finish. So we have the platform installer, and here is where
you can install all the information that you're going to use for creating a web
server out of a Windows machine. Realistically, all you'd have to do is click
Add. Once you have added, you just click the Install button here. It'll show you
any prerequisites that you need and then follow the prompts. With all of that
covered, let's head back to the slides and take a look at what we covered in this
lesson. I'll see you there. Welcome back. Let's go over what we touched on in this
lesson. In this lesson, we talked about installing software, both in theory and in
practice. I hope this clears some things up, and I look forward to seeing you in the
next one.
What We Covered: EC2
Hello, everybody, and welcome back to AWS Essentials. In this video, we're going
to be looking back at everything we covered in this section. Let's get
started. First, we looked into what EC2 stands for and an overview of what servers
are in general. Then we looked at the different flavors that EC2 come in. After
that, we took a look at Amazon Machine Images, or AMIs, and how they work. Then
we looked into EBS and all the different storage solutions that are out there. After
that, we talked about the importance of security groups and why you really want
those roles to be locked down tight. We also looked into auto scaling to see what
scaling in and out can really do to affect your environment. IP addresses came
next, and we looked over how they interact specifically with EC2 instances.
Resource groups and tagging came after that with our focus being on how you
can really keep your environment organized. Then we talked about load
balancing and why you really need to take that into consideration when you're
building out your environment. After that, we jumped into the more granular
topics, how to create an EC2, how to connect to them, and how to install software
on them, which leads us to here. I hope the section was helpful and cleared some
things up. I look forward to seeing you in the next one.
Storage Services
An Overview of Storage Services
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over what we're going to cover in this section, what S3 stands for, and
some of the reasons why you might use it. Let's get started. So here's what we're
going to touch on in this section. First, we have this video where we're going to
go over what storage services are and what S3 is. Then we're going to move on to
the basics of S3 and what the different components are. Then we'll discuss how
to create buckets, how to set up your permissions on who can and can't access
your buckets, and then we'll be discussing object versioning and easy
encryption. And finally, we'll take a look back on everything we covered in this
section. So S3 stands for Simple Storage Service. And I like to think of it like the
cargo hold. It's virtually unlimited storage for AWS. With each object in storage,
that can be up to 5 TB in size. It's also not a one-size-only storage solution. There
are a lot of options that you can customize to make your storage exactly what
you need it to be. Okay, so now that we have an idea of what S3 is, let's talk about
why you might use it. First off, there's the reliability that S3 has, which is a 99.9%
durability, meaning that there's a very, very small chance of issues, and that's
considered a great option for backups or mission-critical files. You're also less
limited on space in general. Since S3 is basically limitless when it comes to
storage, it's also a much cheaper option for a lot of your storage needs. And
finally, you have easy options for protection on your storage. One-click
encryption, versioning, and simple replication, it's much easier to keep your file
safe, but available. All right, with all of that covered, let's go over what we
touched on in this lesson. First, we talked about what we're going to go over in
this section. Then we discussed what S3 stands for, and then we touched on a
few reasons why you might utilize S3. I hope that cleared some things up, and I
look forward to seeing you in the next one.
Understanding S3 Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about S3 buckets and the customization options that you can have
for them. Let's get started. So first and foremost, let's talk about buckets. Buckets
in general are a great tool. They can hold a lot of liquid or other items. They're
really good for transporting things from one person to another. Things that you
would have too many in your hands, so you can put them in a bucket, hand it to
somebody else, and then they can get the items out that they need. Just like
buckets in real life, the buckets in S3 work in a very similar fashion. If you were to
upload a file into a bucket and then somebody else needed that same file, they
could easily download that file from that same bucket without you having to send
it to them. And because of that, S3 buckets are extremely customizable. There's a
lot of different options that you can use to make them be what you need them to
be. If security is something that you have in mind, they have easy encryption
options. A simple push of a button, and you can encrypt your entire bucket
so that only people with the same key can access it. Or maybe you want a simple
static website, something to say, hey, we have a new product launching or
something along those lines. An S3 bucket is an excellent way to do that as
well. Or if you have data that's really sensitive, there's also versioning
available. Versioning allows you to have multiple versions of a specific object. So
let's say that someone from HR uploaded their annual reports into a bucket and
someone from payroll decided, hey, we need to update this particular figure. They
accidentally updated the figure in the wrong bucket. With versioning, you can
easily find the version that HR uploaded and restore it back to that version
instead of the one that payroll uploaded. So, let's review what we touched on in
this lesson. First, we discussed what exactly are S3 buckets and how they're very
similar to their real-world counterpart. And then we talked about some of the
basic customization options that S3 offers and some of their most popular. I hope
this clears some things up, and I look forward to seeing you in the next one.
Creating Buckets and Objects
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over how to create buckets and objects in S3. Let's get started. So in
this demo, the first thing we're going to do is navigate to the AWS console and go
to the S3 section of the console. Next, we'll be creating a bucket inside the S3
section of the console. And finally, we will upload an object into that newly
created bucket. Let's get started. All right, it's demo time. Now we can jump into
the AWS console and build out that S3 bucket and upload a file. I'll see you
there. So in the console today, we're going to be heading to the S3 section of the
console. If you don't have it in your Recently visited section like I do here, the
easiest way to find it would be to go up to the search bar, type in S3, and click on
S3. So as you can see here, I currently don't have any buckets. This is what your
bucket screen will look like when you actually do have a bucket. But since I don't
have one at the moment, let's go ahead and create a new bucket. We're going to
click on the Create bucket button. And now we're at the bucket configuration
screen. There are a lot of options when it comes to creating your buckets. Let's
start with the first section here. Your bucket name has to be globally
unique, which means that you can't share a name with somebody else. So I'm
going to type in AWSEssentials93 just in case. So these are your access control
lists, whether you have them enabled or disabled. For this particular demo, we're
going to keep them disabled. Here is where you can actually have public access
to your bucket. So by clicking off this button, you basically allow your bucket to
be public, allowing you to do things like host a website. We're going to go ahead
and leave it on private. Here is your versioning section. This is where you can
decide whether your bucket needs to have versioning or not, whether it can keep
objects stored inside of the bucket and keep different versions of that particular
object. We're going to go ahead and leave that disabled at this particular
time. We'll also go ahead and leave encryption disabled, though this is where
you would change it if you wanted to have your items inside of your
bucket encrypted to what you need them to be. So the last thing under the
Advanced settings is going to be Object Lock. So, with Object Lock, that means
that you can put an object into the bucket and then have it locked to be just that
particular thing, which means people can read it, but it can only be written to
once. We'll go ahead and leave that disabled here as well. So we will go ahead
and click Create bucket. And you can't have uppercase letters, which I forgot. So
we're going to go ahead and change that to lowercase, click Create bucket, and
we have our bucket, AWSEssentials93. So by clicking on the name here, we're
able to go into the bucket. And you see here we have no objects inside of our
bucket. If we wanted to change that, we can go to Upload. And there are two
ways you can upload files into this bucket. You can either click the Add files
button here, which allows you to go through your system and see what type
of things you would like to add. You also have the Add folder button if you want
to add more than one item into your bucket. I just have one thing I'm going to
add. I'll show you the second way you can add things, which is to drag and
drop. So after I've uploaded that particular thing, you can see what our
destination details are here. We see Bucket Versioning is Disabled, Default
encryption is Disabled, and Object Lock is disabled. So we're going to click on
Upload, and we have successfully uploaded that file. We're going to click
Close. And now as you can see, our file is right here. You can see how big the file
is, what type of file it is since this is a png file, the access ARN for that particular
file, and the S3 URL if you're going to access it from the CLI. It does not have
public access on it, but the owner has read and write access on it, which is us and
our account right here. We also have versioning disabled, so we don't have any
different versions of this particular item. If we wanted to change that and have
versioning enabled, we could always click the Enable Bucket Versioning
button. Once it is enabled, it can't be disabled, so make absolutely certain that
you want to use versions. Upload the file again, and you see the destination
details have changed, so bucket versioning has been enabled. We click Upload,
click Close out. And as you can see here, we have the current version. We have
the first version that we put in as well. It's labeled null since we didn't have
versioning enabled when we first uploaded this file. Let's head back to the slides
so we can look over what we covered in this particular lesson. I'll see you
there. And welcome back. Let's go over a quick review of what we covered in this
lesson. First, we discussed how to create an object and buckets in theory. Then
we jumped into the console and saw how to do it in practice. I hope this cleared
some things up, and I look forward to seeing you in the next one.
Exploring Permissions Associated with S3
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we'll be
going over permissions on S3 buckets and then jumping into the console to see
how they work in practice. Let's get started. So for permissions, you have three
parts for how they work. First, you have the resource that the permission will be
affecting, whether it be a bucket or a job or an item inside of S3. Then you have
the action that can be taken on that resource, things like listing objects inside of
a bucket, putting new items in it or deleting objects. And finally, you have the
effect that's going to be on the S3 item, whether allowing someone to do an
action or denying someone to do an action. Things like this person is allowed to
put things into this bucket, but they're not allowed to delete anything. All right,
it's demo time. Let's jump into the console and see what permissions look like in
practice. I'll see you there. And welcome to the AWS console. In this demo
today, we're going to be looking at S3 permissions and the Policy Generator. So,
first things first. We're going to go to the S3 section of the console. If you don't
have it on your Recently visited or on your bookmark bar, the easiest way to get
there is to go up to the search bar, type in S3, click on S3. And as you can see, I
currently have one bucket in this particular account. So we're going to click on
awsessentials, and then we're going to click on Properties. So with the
Permissions Generator, you need a couple of resource names in order to get it to
work. One of the first resource names you need is the resource name for this
particular bucket. So we're going to copy the ARN, or Amazon Resource Name, for
awsessentials. Then we're going to click on Permissions, click on Edit. So you can
either do this by adding a statement like this, which allows you to change what
actions and resources you're going to be affecting, or you can get your Policy
Generator to do it for you. So what we're going to do is we're going to click on S3
Bucket, and we're going to put in the Amazon Resource Name here, or the
ARN. And then we're going to say that a certain user can't delete this particular
bucket. But in order to fill out this Principal slot, we need the ARN for that
particular user. So we're going to go back to our S3 bucket here, go up to Search,
type in IAM. Open that in a new tab, and then we're going to click on the Users
button here. And we're going to click on Bree from HR, as Bree from HR
has currently full access into the S3 space, but we don't want her to be able to
delete that particular bucket. So we're going to copy her user ARN, which is this
information right here, go back to the Policy Generator, paste it into the
Principal. Click on Deny, then click Add Statement. Then we get Generate
Policy. So as you can see, here is our statement information, the action that
the statement is for, s3:DeleteBucket. Here is the "Effect" : "Deny", the resource
that we're affecting, which is awsessentials, and the Principal or the user that
we're allowing this to happen to. So what we're going to do is we're going to copy
this, close it out, and paste here in this particular bucket. And then you would
Save changes. And as you can see here, Bree is no longer allowed to delete the
bucket, awsessentials. These policies are editable just by hitting that Edit
button, or you can delete them by hitting the Delete button, typing in delete. And
now there's no policy, and Bree can once again delete that particular bucket. Let's
head back to the slides to see what we touched on in this particular lesson. I'll
see you there. And welcome back. Let's go over what we touched on in this
lesson. First, we talked about S3 permissions in theory, and then we jumped into
the console to see what they look like in practice. I hope this cleared some things
up, and I look forward to seeing you in the next one.
Working with Object Versioning
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over object versioning and then do a quick jump into the console to
take a look at versioning in practice. Let's get started. So let's talk about what
object versioning is. Really, it's the best way to keep your S3 items in your bucket
safe, while having multiple versions of that item means that if something
gets uploaded that wasn't supposed to, you can quickly and easily change the
version back to what it needs to be. You also have more control over who can
change objects inside of your buckets, allowing you to be able to add or
remove versions inside of your bucket. It also helps if something has been
deleted that wasn't supposed to, it can easily be retrieved back just in the nick of
time. All right, it's demo time. Let's jump into the console and see object
versioning in practice. I'll see you there. And welcome to the AWS console. In
today's demo, we're going to be taking a look at object versioning, specifically
what can change in those versions. So what we're going to do is go to the S3
section of the console. If you don't have it on your Recently visited or on your
bookmark bar, go up to the search bar, type in S3. Click on S3, and you can see
we have our awsessentials bucket right here, which already has object versioning
enabled. So we're going to make a test file to get into this bucket. How we're
going to do that is we're going to create a file with the words ACG Test 1. And
then we save that file. Now we go back to the bucket and click Upload. And then
we can upload this file into our section here. Click Upload. We have successfully
uploaded that file. We're going to click on that file, then we're going to click on
Versions. So here is our current version that we have up here, the one that says
ACG Test 1. So now, we're going to change it from ACG Test 1 to Test 2, go back to
the awsessentials, Upload, upload the file here. Now we're going to go back to
Versions. And as you can see, we have two different versions of this file. So what
we're going to do we're going to download this file, open it back up. As you can
see, ACG Test, ACG Test 2. Without actually changing this particular file, we're
going to go back into our bucket, click on ACG Test, click on Versions. So what
we're going to do is delete the version that we currently have. So we're going to
click on the box and then hit Delete. Then we're going to type in, or in this
particular case, copy and paste, permanently delete. Then click Delete. Close this
out. And as you can see, we have the old version of this particular file. So we're
going to go back to the bucket, click on the object, ACG Test, then click
Download. Then we open up the file. And as you can see, ACG Test, ACG Test 1. So
that means without editing the files, we've come back to our ACG Test 1 just like
we had originally inside this bucket. And with that, you know everything you need
to know about versioning. Let's head back to the slides so we can review what we
touched on in this lesson. I'll see you there. And welcome back. Let's go over what
we touched on in this lesson. First, we talked about object versioning in
theory, what it is, and how the different components work. Then we jumped into
the console to see what it looks like in practice. I hope this cleared some things
up, and I look forward to seeing you in the next one.
What We Covered: S3
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over what we covered in S3. Let's get started. So what did we cover in
this particular section? First, we talked about what exactly S3 is and how it
works. Then we got into a little bit more nitty gritty of what exactly S3 does. We
talked about buckets, versioning, encryption, and static website hosting. After
that, we jumped into the console to take a look at how creating buckets and
uploading objects worked. We stayed in the console to take a look at how
permissions are associated with S3, taking a look at how we actually
associate them together and what their uses are. Then we looked at object
versioning in practice, how we can change and restore objects and their versions,
and then we have this video, What We Covered. I hope you enjoyed this section,
and I look forward to seeing you in the next one.
The Virtual Private Cloud (VPC) and How
Networking Works with It
Understanding AWS Global Services
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be touching on AWS's global services, things like data centers and what the
difference between a region and availability zones are. But we're also going to
touch on what we're covering in this section as a whole. Let's get started. Okay,
so to get this part out of the way, we're going to talk about what we're going to
cover in this section as a whole. The first thing is this video here where we're
going to talk about AWS's global services, things like regions and data
centers. Next, we'll be talking about understanding VPC basics where
we're talking about what a VPC is and how they work. After that, we're going to
talk about gateways, what they are, and how they work. We're also going to talk
about route tables and how they interact with the rest of your environment. We're
also going to talk about NACLs, or network access control lists, and how they
keep your environment safe. We're also going to talk about subnets, subnets
being the thing where you actually build your environment out in. Then we're
going to go into a bit more detail about availability zones inside of a
VPC, understanding how Route 53 works. And then finally, we'll do a quick wrap-
up in what we covered in this section. But let's go on to the actual lesson. So,
what exactly is a data center? A data center is a collection of servers. It is the
physical location where all of your servers are stored. When most people think of
servers, they think of a singular device inside of the cloud. But in reality, all of
those servers are held somewhere. Usually it looks something like this, a large
room filled with these large cabinets with lots and lots of servers inside them. And
each of those individual servers where you see those blue lines coming out, each
of those can hold a lot of different cloud machines. So, now that we understand
the basics of what a data center is, let's talk about what a region versus
availability zone is. So first, you have regions. So when it comes to a region, that's
the physical location where the data centers are located. So think North Virginia
or Ohio or even Ireland. An availability zone is one or more data centers
with redundancies to make your environment safer, but they're all stored in
separate facilities. So you're likely to have one or more data center per
availability zone and at least two availability zones per region. Okay, let's have a
quick rundown of what we touched on in this lesson. First, we talked about what
we're going to cover in this particular section, then we talked about what exactly
a data center is, and then we took a breakdown of what exactly is the difference
between a region and an availability zone. I hope this cleared some things up,
and I look forward to seeing you in the next one.
Understanding VPC Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about VPCs, what they are, how they work, and what resources you
can put inside them. Let's get started. Okay, so first and foremost, VPC, what does
it stand for? VPC stands for virtual private cloud, and I like to compare it to one of
these side rockets here. It's really important for your ship as a whole, but it's not
the only way to make your ship fly. Realistically speaking, your VPC is going to
contain a majority of your AWS resources. Things like EC2s, RDS instances, even
S3 buckets can be held inside of a VPC. VPCs also allow you to have more control
over your environment as a whole. This means specifically that you can control
who connects to what and when inside your own environment. Okay, so let's talk
about VPCs in a little bit more abstract form. Let's say that this cloud here is your
VPC. Inside that VPC, we have all of these resources. You have an S3 bucket, your
RDS instance, and an EC2 instance. Because all of these instances are in the
same VPC, that means that they can all talk to each other. And because they can
all talk to each other, that means that EC2 instance can use pictures from the S3
bucket to load on a website for a sale. And that RDS instance can be used
to actually access people's customer data. All right, it's demo time. Let's jump into
the console to take a look at what VPCs look like in practice. I'll see you
there. Hello, everybody, and welcome to the AWS console. So in this console, we
are going to be taking a look at VPCs and what a VPC looks like inside of this
section. So if you don't have VPC on your little bookmark bar here or in your
Recently visited, the way you can get there is go up to the search bar, type in
VPC, click on VPC. And now we have our VPCs. So since I'm in the sandbox, I have
one VPC already made. It's in us-east-1. There's also another one in Osaka. That
one in us-east-1 has six subnets. But let's take a look at the dashboard for a little
bit longer first. You also have our DHCP options. We don't have any NAT
gateways. We have one set of NACLs and three security groups. So we're going to
go over to Your VPCs, which is over here on the left and click on the VPC ID
here. That way we can get a few more details about it. So, as you can see, we've
got our VPC IPv4 address. It's a /16. That means it has quite a few IP addresses
available for us. In this section, you can also edit your VPC settings, so changing
your DHCP options. Okay, and so from here, let's create a VPC. We're going to
click Create VPC. We're going to keep highlighted VPC and more, and here is the
map of what our VPC is going to create. We have the VPC. We have our public
subnet and a private subnet. Then we also have it for our public and private
here. We have our route table, which is the route table for our public
subnet, which go out to an internet gateway, which we'll be learning about in
another lesson. And then we have our two private route tables, which go out to
a VPC endpoint, which points at an S3 bucket. We're going to go ahead and leave
this at project, but we are going to change the CIDR notation from 16 to 24. Now
the reason we're going to do that is if you'll take a look over here, you see that it
currently is allowing 65,536 IP addresses with this /16. We really don't need that
many, so let's drop it down to 24, which drops this down to 256 IPs. Pretty
useful. Now for availability zones, it's usually always best practice to have at least
two. You can bump it up to three if it becomes really important or if you need
to have that extra bit of stability, but generally speaking, you need at least two. So
the number of public subnets, we're going to go ahead and leave at 2. That way,
we can have instances that point out to the internet, as well as instances that are
say behind the internet. So, that's these private subnets here. We don't
necessarily need a NAT gateway. And don't worry, we'll be learning about
gateways in another lesson. And we'll go ahead and leave the VPC endpoint over
here at None since we don't need one of those either. Then we're going to leave
on DNS hostnames and resolutions. If you had a website, you would need this
section turned on so that it would be able to resolve properly. So we'll go ahead
and Create VPC. Now this can take a minute. But once it's created everything as
it's going down this checklist here, we can see that it's made our new VPC. And
there we have it. Here is our project VPC with our 10.0.0.0/24 CIDR. It does not
have an IPv6 pool with our main route table and our network access control lists
here. So with that all covered, let's head back to the slides to look at what we
touched on in this lesson. I'll see you there. And welcome back. Let's do a quick
rundown of what we covered in this lesson. First, we talked about what a VPC
is. Then we talked about how you could use it. And finally, we took a look at VPCs
in the console. I hope this cleared some things up, and I look forward to seeing
you in the next one.
Utilizing Gateways
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we'll be
talking about gateways, their different uses, and what exactly they are. Let's get
started. So in this course, we'll be talking about three main types of gateways, the
first being transit gateways, the second being network address translation, or
NAT, gateways, and finally, we'll talk about internet gateways. So first, let's talk
about transit gateways. The main purpose for this gateway is to be a
communication point between your on-premises resources to connect into your
cloud. It can really help simplify those connections since it's just one routing
point that you're using. It also allows for much better visibility over your overall
environment. Since you can get a look at what your on-premises device is, as well
as your cloud devices are looking like. It can also be really useful for scaling. So as
you scale out into your on-premises or in your cloud, you only need to scale your
transit gateway to scale with that. But let's give a more visual example. So you've
got your data center and your cloud and you really want these two things to
connect together, and the best way to do that would be through this Transit
Gateway. Your cloud and servers can send information to that Transit Gateway
and IP address and easily get information back and forth without having to cause
too much trouble. Now let's touch on NAT gateways. NAT gateways, you can have
two different types of connections, a public or private connection. With the
public NAT gateway, you get to have your instances in a private subnet to have
access to the internet without connections coming in. You can also have a
private connection, which allows you to connect to your private subnet instances
to your on-premises instances or your other VPCs. The simplest way to describe
this would be your cloud-to-cloud connection. Realistically, you'd be connecting
from one cloud into a NAT gateway, and then that NAT gateway can connect you
into another cloud. And finally, we have an internet gateway, which allows your
public subnets to connect to and from the internet. You can have one internet
gateway that is the outpoint for several different VPCs. All right, it's demo
time. Let's jump into the console and take a look at some of these gateways. I'll
see you there. And welcome to the AWS console. In today's demo, we'll be talking
about the three different types of gateways, NAT gateways and transit
gateways. I've shown you before how to create an internet gateway, so we'll be
focusing mainly on creation for the NAT gateway and the transit gateway. But in
order to start this process, we need to get to the VPC section of the console. So,
if you don't have it in your Recently visited or under your bookmark bar, you can
go up to the search bar, type in VPC, click on VPC. And over here on the left-
hand side, you can see where it says NAT gateways. We're going to click on that,
and we are going to create a NAT gateway. This NAT gateway will be private, so
it'll just connect to other private resources. So we're going to name it Nat. We're
going to choose which subnet for it to be in. We're going to choose one of the
subnets that we made in a previous video, being sure to grab a private subnet for
this particular gateway. And we're going to leave the connection type Private. If
we do that, then the NAT gateway cannot reach the internet. However, if we put
it Public, we would allocate an Elastic IP address to this NAT gateway and
which would allow it to actually see the internet gateway, but we're going to go
ahead and leave it Private. So we're going to create a NAT gateway, and there we
have it. That's how you create your first NAT gateway. At the moment, this
particular gateway isn't connected to anything. We'll go over in the next lesson
how to connect it into a different route table so that way you can actually
connect it into resources. If we scroll down even farther, you can see our Transit
gateways. So we're going to talk about how to create a transit gateway next. We're
going to go up to Create transit gateway. We're going to call it Transit. Since we
don't have an ASN, we are going to leave the rest of these options open. DNS
support allows it to be findable. Default route association means that it's allowed
to be on our default route. And default route propagation means that it will
automatically be on that particular route on that particular route table. If we were
connecting to other resources in a different account, we could also click this
particular button, which would auto accept shared attachments, but we're not
doing that, so we'll leave that as blank and make our transit gateway. Give it just a
little bit as it's going to be in the Pending state for a while, then it'll jump up to
Available. And there we have it. It is now in the Available state. And with that, we
should be able to head back to the slides and take a look at what we touched on
in this lesson. I'll see you there. And welcome back. Let's go over what we
touched on in this lesson. First, we talked about the different types of
gateways, NAT, transit, and internet. Then we jumped into the console to take a
look at how to build out these resources. I hope that cleared some things up, and
I look forward to seeing you in the next one.
Exploring Route Tables (RTs)
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over route tables, what they are, what is routing as a whole, and
jumping into the console to see what they look like in practice. Let's get
started. So route tables, what exactly are they? There are a table or a list of
directions for your environment, which can mean anything from as simple as your
instances finding the internet or as complex as them seeing other VPCs. A route
table can also point to a number of different locations that can be destination
spots specifically for your network. Think VPC endpoints or S3 endpoints. So, now
that we know what a route table is, let's take a step back and talk about what is
routing as a whole. Routing is a way for our network to select paths to get to
places that we want to go, kind of like a map, where a route table is kind of like an
address book that tells you all the endpoints of where you're traveling to. So let's
talk about why routes and route tables are important. In the overarching process
of working with the internet, there's a process called DNS lookup, DNS standing
for Domain Name Systems, which is the way you find basically anything
online. There are three orders of magnitude when it comes to this lookup. The
first and biggest is DNS as a whole, which incorporates just about everything
online. I like to phrase it like a galaxy. It has just about everything in it, and you
can get there, but it might take a little bit. Then you have Route 53, which is how
your account adds to the galaxy of names in DNS. It's more local than DNS as a
whole, but still account wide. So, like a solar system, it's local, but still pretty
vast. And don't worry, we'll be going over DNS and Route 53 in more detail in the
Route 53 video. Then finally, you have route tables, which is the most local of the
three. It can work with something as simple as only one or two VPCs, or it can
become an interconnected web. That's not quite as wide as Route 53, but still
pretty vast. All right, it's demo time. Let's take a jump into the console and take a
look at route tables in practice. I'll see you there. Welcome to the AWS console. In
the console today, we're going to be looking at route tables specifically. In order
to get to the route table section of the console, we need to get to the VPC
section of the console. If you don't have it on your Recently visited section or in
your bookmark bar, the easiest way to get there is to go up to the search bar, type
in VPC, click on VPC, and that'll bring you to the VPC home page. So, from the
VPC home page, if you go over here on the sidebar, you can see Route
tables. We're going to go ahead and click on Route tables. And I've made a
couple of route tables to show what they can potentially look like. So as you can
see, the project VPC has two different route tables. It's got one for private use
and one for public use. And let's click on Routes for this public use. And we can
see that it currently has two routes in this route table. What you see here with all
of these 0s is going to be the default route. Basically, it's where things default to
if they don't have something in the other route that is available to them. So if
something is looking for an address that doesn't fall into the 10.0.0.0/16 IP range,
the default goes to the 0 address, which is the internet gateway. So it goes and
looks for it outside of our network. I've added a couple of different options when
it comes to this particular route table. First and foremost, you see that it still has
the local route table, which is that 10.0.0.0/16 address. But here for its default
address, it has a NAT gateway. This default allows you to connect outside of your
VPC, connecting into another VPC to connect to private instances. But think of it
as kind of like an internet gateway, but private. This also has a linked VPC, so the
default VPC, which you can see here and here. Our private route table for
this project VPC has access to one of those VPCs, so that way resources inside of
that private network can see things inside this network. In this particular case, it's
also going to S3, which is really useful for things that need to be pushed into
S3. You can also see your endpoints by just clicking over here on Endpoints. You
can see your internet gateways by going into Internet gateways here. As you can
see, we have the Project-igw right here. And then back to Route tables to take a
look at one more thing. As you can see here, this is not considered the main route
table. The main route table is considered to be the default for the VPC. That can
be changed, of course, inside of Actions, but it might be necessary for certain
types of subnets. So the other thing that you can see when looking at this
particular route table is what subnet is associated with it. We click on Subnet
associations. And we see that, hey, it is the project's public1 subnet. And you're
able to see that with the private as well. Project-subnet-private1-us-east-1a. And
this is the network information for that particular subnet. You can see that
currently the only tags associated with it is the name for this particular route
table, which is just fine. However, it can be really useful to have more information
about what's going on with your route table and where they're needed in the
organization as a whole. You can add routes into your route table by going to Edit
routes, Add route, and then adding which type of route you're wanting it to go
to. As you can see, they show you what exactly you're adding to. You can say,
hey, this is adding an S3 bucket, this is adding some CloudFront information, and
this is adding some DynamoDB information. If you're wanting to add a default
route, specifically so it will go to that NAT gateway so that way it can connect to
other private VPCs, for the ending here, you would just click on the 0/0 route and
then click what you would like it to go to. So if you're wanting to connect it to
another VPC, you would click Peering Connection. And then you would click the
VPC that shows up in this particular drop-down. I don't currently have any of
those set up at the moment, so we're going to just click X. You can also point it at
specific instances or just have it as being specifically only a local network. We're
going to hit Cancel. Theoretically, if you wanted to save those settings, you would
hit Save, and there we go. So now you know how to add a route to your route
table, though generally speaking, you don't necessarily need to do that unless
you're adding it to a specific VPC endpoint. The route tables can be really useful
for things like connecting instances together or connecting VPCs
together. Although not required, it is considered best practice to customize your
route table to determine where your network traffic for your subnets or gateways
are going. Let's head back to the slides to take a look at what we learned in this
lesson. I'll see you there. And welcome back. Let's do a quick rundown of what we
covered in this lesson. First, we covered what is a route table? Then we
covered what exactly is routing? And finally, we jumped into the console to take a
look at what route tables look like in practice. I hope this cleared some things up,
and I look forward to seeing you in the next one.
Reviewing Network Access Control Lists (NACLs)
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over NACLs, what they are, and how they work in practice. Lets get
started. So, what is a NACL? NACL stands for network access control list, and
they act as a firewall, controlling the traffic on your subnet level, ensuring only
the traffic that you want to come into your environment actually comes in. They're
also really useful for subnet control as you can have a NACL that supports
multiple different subnets. So that way, you don't have to keep adding
those particular rules into your subnet listings. All right, it's demo time. Let's take
a look at NACLs in practice. I'll see you in the console. And welcome back to
the AWS console. In the console today, we're going to be looking at network
access control lists, or NACLs as they're called. These NACLs are usually found in
the VPC section of the console. So that's where we're heading to today. If you
don't have it under your Recently visited or under your bookmark bar here, you
can always go up to the search bar, type in VPC, click on VPC, and that gets us to
the VPC home page. So from this page, as you can see over on the left-hand side
here, we have under Security, we have Network ACLs, or access control
lists. We're going to click on that. So realistically, there are two different ways you
can go about this. You could either edit a pre-done NACL. This is the one for the
default VPC that's currently in North Virginia, or you can create a new ACL by
clicking on this button here. We're going to set it for the default VPC. We're going
to call it NACL2 and Create network ACL. All right, so we're going to highlight
this. We're going to edit the subnet association. So what subnet association
means is what subnets are associated with this particular network access control
list. And we are going to click on all of the subnets that are currently here. Though
if you're wanting to get only a certain number of them, just clicking one or
two, you can obviously have just these four. Or if you really wanted to, you could
just have one network that this particular NACL is associated with. Like if you had
one particular instance and one particular subnet that you wanted to have a
different network access control list, this would be how you would handle
that. We're going to go ahead and Save changes. All right, now we're going to edit
some rules. So as you can see, there is currently one rule inside this network
access control list. It is the default rule. It is all traffic on all ports is denied. This is
not an editable rule. Since by default the rule is to deny all traffic, we need to add
a rule in order to make sure that we can access associated subnets. This is why
it's really important to check your NACLs and your security groups first whenever
you're having connectivity issues. These rules can get a little bit complicated if
you don't monitor them closely. So if we wanted to add a rule, we would have to
add a rule number, and they start at 100 for your top rule. And let's say that we
wanted to make sure that people could get in on port 80 on any of the actual IP
addresses, and we want to allow that traffic. Then we would add a second rule.
We would put 110, and this is the next rule down. So, when you think of the
network access control list, think of it following like a table inside of a database. If
your rule doesn't match the first line, it'll go to the second line. If it doesn't match
the second line, it'll go to the last line. So we're going to put this for HTTPS traffic,
again, Allow. And then the final rule that we are going to add in here, 120.
We're going to do SSH traffic, and we're going to allow for this. Normally, I would
highly recommend that you change this. Instead of it being all traffic, you would
just allow traffic from your home network or wherever you're logging in from. But
since this is a demo, we're going to just leave that at 0 since this is all going to
get wiped out later. So we'll go ahead and Save changes. And as you can see, in
our inbound rule, we now have quite a few different rules here. We have it open
on port 80, port 443, and port 22. Now our outbound rules is basically saying that
it doesn't allow traffic in general. Let's change that. So this is coming from
instances inside of this network going out. So let's add a new rule. And let's say
that we want all traffic to be allowed out. Oops, make sure that you put a rule
number on that for that. So we're going to put 100 and Save changes. Now this
outbound rule means that any traffic that comes from inside of our network will
be allowed outside of the network, which is important for things like websites and
the like. Now you can do the same thing when you're editing a NACL that's
already in place. As you can see, this already has a 100 rule, allowing all traffic
in. It also has the same outbound rule that we added, which is all traffic is allowed
out, and it is associated with all the subnets we didn't add to the other NACL.
If you wanted to edit these rules, it's the same thing. We just click the Edit
button. Add a new rule. The rule is 110. Let's do SSH, Allow, and Save changes. See,
now we've got the SSH rule, but generally speaking, this isn't actually necessary
because you have all traffic is allowed coming in for your first rule. So, this rule is
now redundant. So let's say that we wanted to get rid of that rule. What we can
do is Edit inbound. We can click this Remove button here, and then click Save
changes again. And we are back to our two-rule setting here. That should clear up
everything you need to know about NACLs. Let's head back to the slide so we
can take a look at what we learned in this lesson. I'll see you there. Ad welcome
back. Let's do a quick rundown of what we covered in this lesson. We touched on
what NACLs are in theory, and then we jumped into the console to see what
NACLs are in practice. I hope this cleared some things up, and I look forward to
seeing you in the next one.
Working with Subnets
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about subnets, both in theory through the slide deck here and in
practice by jumping into the console. Let's get started. First and foremost, let's
talk about the benefits of subnets. Subnets are the places where your resources
reside. Inside your VPC, your subnet is where you're going to build out all of your
resources. Subnets also allow for more security, keeping your private networks
private and your public resources public. First, let's talk about how traffic flows
inside of your subnets. So in this example, you can see a public and private
subnet. And what you can see here is the traffic flowing to different parts and
pieces of the network from different places. Your public subnet flows from the
subnet past your NACL into a router. That router points it to an internet gateway.
That internet gateway gets it out towards the internet. That allows the internet to
flow back and forth for this public subnet. Your private subnet has to go through
a different set of NACLs. It reaches out to a NAT gateway. That NAT
gateway reaches out to that same router. But instead of heading out to that
internet gateway, that router can easily point it back to one of the EC2 instances
that are inside that public subnet. So as you can see, with a subnet, you can still
have traffic flow into other subnets. It just requires a little bit more workaround
in order to get it to work properly. All right, it's demo time. Let's jump into the
console and take a look at subnets. I'll see you there. And welcome to the AWS
console. In the console today, we'll be taking a look at subnets and how
to manually create them inside the VPC section. So in order to get there, we're
going to go to the VPC section of the console. If you don't have it in your
bookmark bar or in your Recently visited, what you can do is go up to the Search
menu, type in VPC, click on VPC. We currently have two VPCs in North
Virginia. We can see that by going to our VPCs, and we have these two VPCs, the
default VPC and a Test VPC. But that Test VPC doesn't have any subnets
currently associated with it, so let's change that. On the left-hand side over here,
we're going to click on Subnets, then we're going to click Create subnet. We're
going to select our Test VPC. All right, the CIDR notation for this VPC is /16, so
any subnet that we put inside of here has to be smaller than the 16. And with
CIDR notations, when I say smaller, I mean the number on the side has to be
bigger. So we're going to title this My-subnet. Let's go ahead and put it in us-
east-1f, and we'll go ahead and put it as 10.0.0.0/24, then Create subnet. And just
as simple as that, we see that it's currently in our VPC Test. Our subnet ID is this,
and it has 251 available IP addresses. So right now, this particular subnet is
private. In other words, it doesn't have access to the internet. To make it public,
we would first need to create an internet gateway and establish the route that
goes to that internet gateway from the route table. And with that, let's head back
to the slides to see what we touched on in this lesson. I'll see you there. And
welcome back. Let's do a quick rundown of what we covered in this
lesson. First, we talked about what subnets are in theory, going over why
traffic flows inside of them and what they realistically do. Then we looked at
subnets in practice by jumping into the console and taking a look at them there. I
hope this cleared some things up, and I look forward to seeing you in the next
one.
Understanding How Availability Zones Work inside a VPC
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about availability zones inside VPCs and what they look like in the
console. Let's get started. So, let's talk about availability zones. Availability zones
are bubbles inside of subnets that your resources are built in. It allows you to
have high availability as it allows you to build resources in different zones to
prevent outages. It also allows for redundancy, so that way just in case something
happens, you always have a backup just ready to go. All right, it's demo time. Let's
take a look at what availability zones will look like in the console. I'll see you there.
And welcome to the AWS console. In the console today, we're going to be looking
at availability zones inside of a VPC. So in order to take a look at that, what we're
going to do is go to the VPC section of the console first, which if you don't have it
in your Recently visited or in your bookmark bar, you can easily find it by going up
to your search bar, typing in VPC, and then clicking on VPC. So from the landing
page here, what we're going to do is we're going to create a new VPC. And as you
can see here, we can see that there are a number of availability zones
available for us to edit under the VPC and more section. If we just go under VPC,
we do not get an option to edit this particular metric. So it's really good to do that
VPC and more when you have the ability to. Choosing the number of availability
zones dictates how many subnets you have across those availability zones and
how many subnets you'll have inside them. So, let's say we wanted to do three
availability zones, and they are a, b, and c. But in us-east-1, we have other options
for where we can put that. So instead of putting it in us-east-1c, we can put it in
1f, 1e, and 1d. So it's in d, e, and f rather than a, b, and c. As you can see here, we
have six subnets, three public, and three private across three availability zones,
each of the private subnets getting their own route table and all of the
public subnets going off of the public route table, going out to an internet
gateway. We'll go ahead and create this VPC, and it might take a minute for it to
create. So I'll come back in just a moment once everything is made. So once
everything has been created, we just click on the View VPC button. And from this
screen, we can't really see how many availability zones we have available to us. In
order to get a better grasp of that particular concept, we're going to go to the
EC2 section of the console and launch an EC2 instance into one of our new
availability zones. So how we're going to get there is go up to the search bar, type
in EC2, click on EC2, and then we're going to click on Launch instance. So we're
going to name this server. We're going to leave it Linux. We're going to leave the
key pair and instance, typing the same. The only thing we're going to edit is the
network settings here because as you can see, it's going into the network
default rather than that new VPC that we created. So we're going to click on that
new VPC, and there we have our new subnets and availability zones. We'll go
ahead and shove this particular instance into a public subnet in the 1f availability
zone, and click Launch. All right, and there we have it. We have launched a new
instance into that particular availability zone that we just created. And as you can
see here, it's listed our availability zone as us-east-1f. And with that, let's head
back to the slides so we can take a look at what we learned in this lesson. I'll see
you there. And welcome back. Let's do a quick rundown of what we covered in
this lesson. First, we talked about what availability zones are in theory. Then we
jumped into the console to see what they look like in practice. I hope this cleared
some things up. I look forward to seeing you in the next one.
Understanding the Basics of Route 53
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over Route 53, how it works, as well as what some of the most popular
record types are. Then we jump into the console to take a look at what those
record types look like in practice. Let's get started. So what is Route 53? Route 53
is a way to control your network traffic, mapping domain names to IP
addresses. So what you would type into your internet browser is the domain
name, and that gets translated to an IP address of a server. But speaking of
that, let's talk about some of the more popular record types for those IP
addresses. First, we have address records, or A records. They point to an IP
address from that domain name. For example, if you're going to Google, that isn't
actually what the computer is going to be looking for. The computer will look for a
specific IP address that is associated with it. And then we have Canonical Name
records, or CNAME records. These allow your domain names to point to a specific
place. The most common use of this is if you have a website with www. in front of
your website name and your customer just puts in your domain name. With a
CNAME record, you can point them to the correct record without having to
redirect your information. You also have name servers, which keep track of where
the records need to be within a domain and where the domains need to be
pointed to. And finally, we have mail exchange records, or MX records. These are
the types of records that you use for custom email servers. All right, it's demo
time. It's time to take a jump into the console and take a look at those records and
Route 53 in practice. I'll see you there. And welcome to the AWS console. In the
console today, we're going to be taking a look at Route 53 and what
network addresses look like in the console. So first and foremost, we're going to
go to the Route 53 section of the console. If you don't have it in your Recently
visited section, the easiest way to get there would be to go to Search, Route,
Route 53. Here we are on the Route 53 dashboard. So let's make a new hosted
zone as that's where we're going to have all of our DNS records and the like. What
we're going to do is we're going to create a new hosted zone. We want to create a
private hosted zone with the domain name AWSessentials. All right, we're going
to choose our VPC, and the region is going to be N. Virginia. We're going to use
our Test VPC and Create hosted zone. As you can see, it adds already for us the
name servers that are here, name servers for AWS. So let's say that we wanted to
create an A record for this particular section. So what we're going to do is create
a record. So this is going to be the root domain for AWS Essentials. It's going to be
the A record here. So we need to have an EC2 that actually is acting as our web
server. So we need an IP address that we're going to use for this particular
instance. So to do that, we're going to go to the EC2 section of the console. If you
don't have it here on your bookmark bar, you can always find it through the
search bar, but we're going to open it in a new tab. Click on Instances, and then
click on this server here. As you can see, this server has a public IP address, so
we're going to copy that public IP. Go back to the add record. That value is going
to change from nothing to that IP address, and click Create record. So now we
have an A record for this particular ID. Now normally if you're doing this inside of
a public zone, you would have the .com or .org at the end of the
awsessentials. Since we're doing this in a private zone, we don't need that on this
particular setting. You can also import zone files if you already have a
particular domain in somebody else's care. So like let's say you're moving from a
different domains' hoster to AWS, you can always copy and paste your zone file
into this particular section, and it will create your zone records for you. All you'd
have to do is click that little Import button. And of course, you can create all sorts
of other types of records as well. You can create CNAME records like we talked
about in the slides or MX records if you're trying to get a mail server started. You
can also do things like PTR records or TXT records if you're using things
specific for SSL or verifying senders. And now you've built out your first set of
records. Let's head back to the slides to see what we touched on in this lesson. I'll
see you there. And welcome back. Let's do a quick rundown of what we covered
in this lesson. First, we talked about what Route 53 is, and then we looked at
some of the different types of records that are possible with Route 53. Finally, we
jumped into the console and took a look at what those records and Route 53 look
like in practice. I hope that cleared some things up, and I look forward to seeing
you in the next one.
What We Covered: VPC
Hello, everybody, and welcome back to AWS Essentials. In this video, we'll be
doing a quick review on everything we touched on in this section. Let's get
started. In the first video of this section, we talked about AWS global services like
availability zones and data centers. Then we talked about VPC basics like how to
make a VPC. After that, we talked about utilizing gateways and how they allow
access to things in general. Next, we discussed route tables and how they work
on a broad scale. Then we talked about network access control lists, or
NACLs, and how they keep your environment safe. After that, we talked about
how to divide your environment up into sections with subnets. We also covered
availability zones in more detail and how they work inside of the VPC. And then
we took a look at Route 53 and DNS in detail. And finally, we have this video,
which was a quick recap of everything that happened in this section. I hope this
cleared some things up, and I look forward to seeing you in the next one.
Database Services
An Overview of Database Services
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're
going to be going over what exactly we're going to touch on in this
particular section, as well as what exactly is a database. Let's get started. But
before we get started into the lesson proper, let's take a look at what we're going
to be covering in this section as a whole. The first thing that we're going to cover
is this particular video where we're specifically going over what exactly is a
database and how do they function? In the next video, we'll talk about RDS and
how it works and how it's different from a regular database. After that, we're going
to talk about DynamoDB and how it's set up. And finally, we're going to go into
the console and talk about how to actually build out an RDS instance and take a
look at what exactly it looks like to build out from the console. So let's get started
in the lesson. So when I think about databases, I think of them as the side rocket
here. They're a really important part to how the rocket moves and how it interacts
with everything. And it's part of the process of what people think of when they
think of a spaceship. In the context of AWS when we're talking about databases,
realistically, they are an organization of collected data, so they can be just about
any kind of information you can think of. They also have the option of being a
server or a serverless section, which means that they can be a traditional style of
database, which is you have it on an actual instance, or it can be a serverless
style of database, which is a more specialized version of databases. Okay, but
before we dig any deeper, let's talk about what exactly is a database? The
database realistically is a collection of columns and rows of specific types of
information. And those columns and rows can be organized in ways that allow you
to gain more information more quickly. But realistically, that information can be
just about anything, anything from invoices to your favorite restaurant's menu or
even as simple as a list of names and birthdays. And I bet you're thinking, well,
why would I need this information? Why would you need a database? Databases
really come in handy with things like back ends of stores to use as inventory or if
you're keeping track of a userbase for a website. Databases can be incredibly
useful and incredibly powerful tools to help their users and the people supplying
users with information. So let's review, what exactly did we touch on in this
particular lesson? The first thing we touched on was what exactly we're going to
cover in this section as a whole. Then we talked about what exactly is a database,
and then we talked about why exactly you would use a database. I hope this
cleared a few things up, and I look forward to seeing you in the next lesson.
Understanding RDS Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about RDS and what languages you use to interact with it. Let's get
started. So, what exactly is RDS? RDS stands for Relational Database Service. As
we discussed in the last video, a database is a collection of data. In a relational
database, it means that data can be referenced by other data points. So why
would you use RDS instead of just installing a database software on an EC2
instance? Well, with RDS, AWS takes care of all the underlying hardware
monitoring, specifically when you're looking at things like utilization. Or if your
underlying hardware just isn't up to snuff, you don't have to worry about it. All it
would take was AWS noticing it. It's also easier for you to scale for your needs. Not
as many orders? Well, you can scale down. Getting ready for that really big once-
a-year sale? Well, time to scale up. Okay, so now that we know about RDS
instances, let's talk about the different flavors of databases. First, you have SQL
databases. These are the databases we have been talking about for the most part
so far. They're collections of data set up in tables that can reference each other
or not, depending on if your database is relational or not. Data can be found
through these very complex commands called queries. We'll go over more about
queries in just a moment. You also have non SQL databases. This is the type of
database that isn't really set up like a table like we've been discussing previously.
It's a collection of data that doesn't have any structure to it. It works really well
when you're referencing data for things like PDFs or graphics or if something that
a simple query might be able to find instead. So for these buzzwords besides SQL
and non SQL, you might run up against another acronym, DQL. Don't worry, DQL
just stands for data query languages, and it's the umbrella that SQL falls under. So
now that we have a little bit of better understanding for databases, let's talk
about queries and how to get information from an SQL style of database since
that's what an RDS database is. This is going to be our table. It has two
columns, one for names and one for jobs. In these two columns, we have Bree
who works for HR and Tina who works for IT. Now, let's talk about building a query
to get information from this database. The first option in building a query is called
data definition. This particular query uses commands like create and modify
to add people and jobs to this particular table. Like say we needed to add Steve
from accounting to this database. We would use a definition query to make that
happen. Now you have data manipulation queries. This is where you select or
update data or information. For example, let's say that Bree got HR changed to
people operations. You would use a data manipulation query to update that in
the table, so instead of saying HR, it would say people operations. Then we have
data control, which allows us to control who can see what information on what
tables. And then finally, we have transactional control, which allows us to save
the updates made in the database or roll back changes that shouldn't have been
saved. Okay, so let's review. In this lesson, we touched on what RDS is and what it
stands for, as well as what a database language looks like and how they work
together. I hope this was able to clear some things up, and I look forward to
seeing you in the next one.
Understanding DynamoDB Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over DynamoDB and seeing how it differentiates itself from RDS
instances. Lets get started. So DynamoDB is a database type that varies from
the types that we've talked about before. First and foremost, it's a NoSQL
database, meaning it's not structured like a normal SQL database like we've
talked about previously. It can hold things like PDFs and documents in a non-
structured style. You also deal with a much smaller latency with
DynamoDB, especially since you can utilize tools that AWS gives you like the
DynamoDB Accelerator. So now that we know that DynamoDB is a NoSQL
database, let's talk about the two main types of NoSQL databases. First, you have
the key value pair style, which allows you to associate data as a value and sort it
with its keys, which is great for indexing and making references to other items. But
then you also have the document style of NoSQL databases, which allows you to
have entries into your database that follows a different language like JSON or
XML. It also gives you a much different way to look at your data. So let's talk a
little bit more about that key value pair style of database as that's the category
that you'll see the most often. Take a look at this table. As you can see, we have
three things inbound for our shuttle flight, a package of food, a box of tools, and a
package of parts for the shuttle. Now this table is broken up into three categories,
the partition key, which is where the items are going, in this case, the shuttle, the
sort key so that we can sort the items that are coming in, packages and boxes,
and the value key, which is what the data actually is, food, tools or parts. If we sort
this data, we can sort it by packages, which allows us to see the food and parts, or
we can sort it by box, which will allow us to see the tools. We can also sort by
partition so that we can see what items are coming in at what time, Shuttle-1, 2,
and 3. Let's have a quick review of what we covered in this section. First, we
talked about what DynamoDB is, then we discussed the two main types of NoSQL
databases. I hope this cleared some things up, and I look forward to seeing you in
the next one.
Learning How to Provision RDS
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about how to build out an RDS instance, and then we'll jump into
the console and try it for real. Let's get started. So, building out or provisioning an
RDS instance is fairly straightforward. The first step is logging into the
console, and then we navigate to the RDS section of the console, and finally, we
run the build wizard for RDS. All right, it's demo time. Let's jump into the console
and take a look at provisioning in practice. I'll see you there. And welcome to the
AWS Console. So from the console, we will be heading to the RDS section of the
console. If you don't have RDS here in your Recently visited or here in your
bookmark bar, like it is here, you can always find it by searching for it in the
search bar, typing in RDS and hitting Enter. All right, upon reaching the RDS side
of the console, we're going to go ahead and create a new DB. As you can see
here, we currently have none. So let's go ahead and Create database. We're going
to do a Standard create. We're going to do PostgreSQL since that is one of
the ones that is for our Free tier section, which is this option here. Now you do
have two other options here. You have Production, which defaults the high
availability. It's really important that if you are doing this as a production
environment that you select this option. There's also the Dev/Test section where
it's a little bit less stable, but it still works, and it still works really well. It also
imitates the production environment without having to pay some of the extra
prices for it. Now under the Free tier, we can only do a single DB instance, but
under the Dev/Test or Production, two other options light up. So Multi-AZ means
that it's going to be in multiple availability zones, which is a much better when it
comes to things like preventing outages and the like. The same thing with
clusters. It's much more useful with extra backups and doing things a little bit
safer. But in this particular case, we're going to stick to the Free Tier. We're going
to go ahead and leave the name as database-1. So here's where we get to the
master login. So in order to edit anything inside of this database, you'll need to be
able to log into it first. And that's how we get to these passwords. Now, you can
auto generate a password, which is considered the safest option, or you can
create a password. Either option is fine, though generally speaking, it is safer to
auto generate a password. Though, in this case, I'm going to just make my own
password. All right, we're going to leave it at a burstable class since that's what's
available for our Free Tier. The other two options, Standard is generally speaking
much more useful for the production or the dev and test environments. And
memory optimizes if you're going to have a lot of read writes sequentially, then
you want to have more memory specifically. We'll go ahead and leave storage the
same at the moment. It's allocating us 200 GB of space, which should be more
than enough for most things with a maximum storage threshold of about 1000
GB. Again, it should be more than enough for most things. So here's where you
could connect it to an EC2 if you were using this database as, say, a back end for
a storefront or something along those lines. All you do is connect to an EC2, and
then the EC2 instance you connect to would just be in this drop-down
menu. We're going to go ahead and not do that this time around and just say
don't bother connecting to anything. But we're also going to say it doesn't have
public access. It's going into the default security groups, which is important for
logging-in purposes. And then you have authentication. You have database
authentication with password or password and IAM. You need to have a certain
password, as well as a certain IAM user that can log in or password and Kerberos
options. We're going to go ahead and leave it at Password authentication. So with
the Free Tier, we have 750 hours of Single-AZ dbt2.micro and
dbt3.micro. Everything that we talked about should fall within our Free Tier
standing. We're going to Create database. Now this can take a second as it takes
a little bit for it to install all the software necessary. I'll go ahead and jump back in
once it's finished creating. And after a few minutes, we have our database. So
here's our database information, how much CPU utilization we have, what VPC it's
in, what subnets it's in, and if it's publicly accessible. And with all of that
covered, let's head back to the slides to see what we touched on in this
lesson. And welcome back. Let's go over what we touched on in this lesson. First,
we talked about how to provision RDS instances in theory, and then we jumped
into the console to try it out in practice. I hope that cleared some things up, and I
look forward to seeing you in the next one.
CloudFormation
Understanding the Basics of CloudFormation
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to go over what we're going to touch on in this particular section, and then we're
going to talk about what exactly is CloudFormation and why would you want to
use it? Let's get started. But before we get started on the lesson proper, let's take
a look at what we're going to be covering in this particular section. The first thing
you're going to see is this particular video. We're going to talk about the basics of
what exactly CloudFormation is and why somebody would want to use it. In the
next video, we'll get down to a more nitty gritty feel of how exactly
CloudFormation works, how the template files go into it, and why exactly
it's useful, as well as going into the console and taking a look at how it looks
inside the console. So let's get started with the lesson. So, CloudFormation, what
exactly is it? CloudFormation is an automation tool. It's specifically designed to
help build out resources and to make it faster. When I think of CloudFormation, I
like to think of it as kind of like the cockpit for the ship. Specifically, it's going to
be used to help push the ship where it needs to go. In other words, it allows you
to build out resources without having to manually push the buttons to do it. So
because of that, it means that CloudFormation is a great tool specifically for
automating your environment. It's also a great tool for auditing. It's really good
about keeping track of when and where things get built out at. So, why would you
use CloudFormation? Realistically speaking, automation is going to be safer than
having just a person go through and click the buttons. Human error is a thing. It's
unfortunate, but we have to deal with that. But with CloudFormation, we get to
kind of ease over that. Specifically when you're dealing with CloudFormation, one
of its key points is consistency. When you make a template file and then put that
template file into AWS, it can actually just pump out that same style of
environment every time, which is really handy if you're building a lot of
instances or building in a lot of different places. The other thing that's really
useful about it is security. When you're dealing with templates, and not
necessarily a person going through and clicking the buttons, your template file is
going to be the same every single time. But if you have someone that just, you
know, didn't have their coffee that morning and missed that one particular step
where they have to encrypt that EBS volume, well, now we have to tear down the
environment to put it back up. Thankfully, with CloudFormation, you know it's
going to be the same every time. One of the final notes that I would put for this is
it makes deployments a lot faster. With template files, you can make it so that
you're deploying multiple things at once. So instead of having to go through and
make a VPC and then make an EC2, you can have a singular template file that
has all of that in it, so you set CloudFormation to go, and it goes. You don't have
to think about it anymore. It will build out the resources that you put inside of
that template file. So, let's have a quick review. What exactly did we touch on in
this particular lesson? We talked about what we were going to cover in this
section as a whole. We talked about a general thought process on what exactly is
CloudFormation. And we touched on some of the key reasons on why you would
use it. I hope this cleared some things up, and I look forward to seeing you in the
next lesson.
Exploring How You Would Use CloudFormation
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over what CloudFormation and a cloud template file look like. And
then we're going to jump into the console to see how CloudFormation works in
practice. Let's get started. So, let's talk about template files. In
CloudFormation, you use files in JSON or YAML and can tell CloudFormation what
you're going to build. In this case, the example template file is for an S3 bucket
that's hosting a website, but let's look at this file a little bit more in depth. So here
you have what type of object is going to be built, an S3 bucket, and that it's
available for public reading. This is going to be the files that are made, an index
and error file. And here you have the outputs of the domain name and the URL
for the website. All right, it's demo time. In this demo, we're going to be looking at
CloudFormation in the console, how to build out with it, and how to get to it in
the console. I'll see you there. And welcome to the AWS console. So, for this
demo, we're going to be looking at CloudFormation and how to build out
resources using CloudFormation. But first things first. Let's get over to that side
of the console. If you don't have it in your quick bar like I do here, your best way to
get there would be go up to the search bar, type in CloudFo. There we go. We're
going to click on CloudFormation. And as you can see, we have a couple of stacks
that are already made inside this account. But we're going to make a new
stack. So how you do that is you go over here to where it says Create stack, With
new resources. And here's where we can input our template file. There are
examples that you can use. You can either use a sample template, which are
templates that AWS provides for you. If you wanted something relatively easy and
simple like a specific WordPress blog, you can easily set that up without having to
do any specifics with it. Or you can go into the template designer and make your
template that way. We're dragging and dropping resources to look at it from
there. And from here, you can see this would be the template and your
parameters. And you can add your physical resources that you would be adding
into your template file. I'm going to go ahead and click Close, and we are going to
use a template file that I have premade for this particular example. We're going to
do this S3 file here. If you're uploading your template files into AWS, you can also
view them in the designer as well. But we're going to hit Next, then we're going to
enter the Stack name, which is going to be Mission-Alpha, then we hit Next. So
here's where we can add things like tags and other information. Now, when you're
using a tag, that could be anything from just a name to even your specifics about
what the stack is for. If you have a specific IAM role that you want CloudFormation
to make with these resources, you can add that here. Personally, I just leave that
blank most of the time. Then you have what happens if it fails to build. I'm going
to leave it on Roll back all stack resources. Basically, it won't actually build
anything. It'll just go back to the previous state it was in. You also have the option
of preserving anything that is successfully made, while just having anything that
fails to roll back to its stable state. Okay, with those decided, we're going to hit
Next, then we're going to hit Create stack. So it can take a minute for it to actually
load. So I'll be back with you once CloudFormation is finished building out. All
right, and the CloudFormation stack has finished creating. As you can see here,
there was the S3Bucket CREATE_IN_PROGRESS. The resource creation was
initiated, and the create was complete. Then we had the bucket policies
made, resource creation initiated, and resource complete. So let's go over to the
S3 section of the console and take a look at our new bucket. How we can get
there is we go up to the search bar, type in S3, click on S3. And we see we have
our mission-alpha bucket. And as you can see here, it is publicly accessible,
which is what we need if we're going to be making a website for our bucket. So
with that, let's head back to the slides to finish out this lesson. And we're
back. Let's go over what we touched on in this lesson. We looked at how to use
CloudFormation and what a template file looks like, then we jumped into the
console to take a look at what CloudFormation looks like in practice. I hope this
cleared some things up, and I look forward to seeing you in the next lesson.
Management Tools
An Overview of Management Tools
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over what we're going to cover in the management section, as well as
a general overview of what I mean when I say management tools. Let's get
started. So first things first, let's go over what we're going to cover in this
section. First, you have this video, which will talk about what I mean when I say
management tools. Then we're going to talk about CloudWatch, what it is, and
how its metrics work. After that, we're going to talk about SNS and how it interacts
with some of the other services. Then we'll jump into CloudTrail and see how it
works. After that, we'll talk about the Health Dashboard and how it interacts with
your account as a whole. Then we'll take a look at how to keep your costs in line
with the Cost Explorer, how to keep everything up to date with AWS Trusted
Advisor, and then we'll be looking at some serverless options, as well as some
Lambda basics, then a quick review of everything we covered in this section. So
let's talk about management tools and what I mean when I say that. I break down
management tools into two sections. The first is well, like it says on the tin, it
manages your account, things like Cost Explorer and CloudTrail that allow you to
see what's going on specifically in your account, Cost Explorer, keeping an eye on
exactly how much you're spending, and CloudTrail, which actually follows your
users as they go through the console. But then you also have services that
specifically work with each other, things like Lambda and serverless options that
can send replies and triggers to other services and SNS who can help send
notifications out with CloudWatch to make sure you are always in the know about
what's happening in your account. Okay, so let's go over what we touched on in
this lesson. First, we talked about what we're going to be covering in
this particular section, and then we talked about what management tools are in
really broad strokes. I hope this cleared some things up, and I look forward to
seeing you in the next one.
Understanding CloudWatch Basics
Hello, everyone, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about CloudWatch, what it is, and how it works. Then we're going to
take a look at what CloudWatch alarms look like inside of the AWS console. Let's
get started. So, CloudWatch, what exactly is it? CloudWatch is going to be
your primary monitoring tool inside of AWS. Its main processes are monitoring
your environment to keep track and make sure everything in your environment is
running as smoothly and efficiently as possible. And if something isn't running
smoothly, the second main process of CloudWatch is notification. If one of your
alarms goes off, you can be notified quickly and effectively. That way you can
have much smoother remediation when issues arise. All right, it's demo time. Let's
jump into the console and take a look at what CloudWatch alarms really look
like. I'll see you there. And welcome to the AWS Console. So for this demo, we're
going to be taking a look at CloudWatch. Now if you're not seeing CloudWatch in
your Recently visited, there's a simple way to get there. We're going to go up to
the search bar and type in CloudWatch. Go ahead and click on it, and here is
your overview. So as you can see here, I currently have one alarm that is set and it
is currently in the OK status. The screen is a really good reflector to see what
alarms are going off and what aren't at the moment. You can also see that over
here. As an alarm changes into various statuses, it will change from this section
here, which is the green OK to over here where it's red, In alarm, or here where it's
Insufficient data. This is also where you can see all of your alarms, specifically
your billing alarms or just your devices that are in alarm status. So since nothing
is currently in alarm status, this particular dashboard is empty. But let's take a
look and see what happens if one of our statuses goes into alarm. For this
particular alarm, it was set up to notify us if the server ever goes down. The
instance itself is stopped, so that means that the server has no data available to
it. It's currently giving a state of Insufficient data. That can be seen under here
under All alarms. Because of how this alarm was set up, they don't consider that
to be an actual alarm state. So, this particular field still has nothing in it. This
alarm was triggered by turning an EC2 instance on and off again. And here's what
the status check of an alarm would look like. As you can see, it pops up with a
little red triangle here, and you can currently see it under the In alarm section of
the console. This is usually when you'll get emails that look like this.
These notifications can also be sent to cell phones and a few other devices if you
set up your SNS correctly. Don't worry, we'll be going over what these metrics
mean and how to set up the alarms in the next video, as well as to make sure that
you have SNS correctly set up so that you get these emails when these alarms
go off. With all of that said, let's head back to the slides so we can review what we
touched on in this lesson. I'll see you there. And welcome back. Let's go over what
we touched on this lesson. First, we talked about what CloudWatch is and why it's
really important that you utilize it. Then we jumped into the console to see what
alarms look like in practice. I hope this cleared some things up, and I look forward
to seeing you in the next one.
Utilizing CloudWatch Metrics and Alarms
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about CloudWatch metrics, what they are, how they work, and then
we'll jump into the console to see how those metrics work in practice. Let's get
started. So, what are CloudWatch metrics? Metrics are a great way to keep track
of your resources and account as a whole, something as wide as CPU utilization
or something as granular as the bill for your overall account. With CloudWatch
metrics, you can see all the teeny tiny pieces that make up your account and get
quick notifications if something goes out of what you expect. All right, it's demo
time. Let's take a jump into the console and take a look at what CloudWatch
alarms actually look like. I'll see you there. Welcome to the AWS console. So we're
going to be taking a look at CloudWatch metrics, specifically how to create
alarms and what particular alarms you can create. So if you don't have
CloudWatch here on your Recently visited, the easiest way to find it is going up
to the search bar, typing in CloudWatch, and hit Enter. So as you can see, we
currently don't have any alarms set up for this account, but we do have some
options for alarms if we wanted to make them. Let's go ahead and make an
alarm. So we're going to create an alarm, and we're going to click this button that
says Select metric. So as you can see, there are a lot of metrics that you can use
for your alarms, anything from specific TrustedAdvisor categories to something as
simple as an EC2 instance metric, specifically looking at things like if the
instance doesn't turn on or if the CPU is over utilized. So as you can see
here, there are a lot of different metrics that can come up on these particular
instances. And that's just EC2 and TrustedAdvisor. You even have things for the
more granular subjects like even Polly has potential things you can actually alarm
for. But let's take a look at something that's a little bit more overarching. Let's go
into Billing. Even in Billing, you have different options. You can either do by the
service. In other words, if you get estimated charges of over a certain amount in a
certain resource, like let's say you didn't want to go over $15 in RDS. Click this
little check mark here. And let's say we also wanted it for EC2. EC2, search. So the
search function can also help you find specific metrics that you're looking for. So,
we're going to click on EC2 as well. And as you can see, there's a little blip here
stating that there's an EC2 currently running where we don't have anything for
RDS because we don't have an RDS instance running. Since you can only have
one metric per alarm, I'm going to go ahead and undo RDS and just keep EC2. So
we're going to do this as an estimated charges for EC2. We're going to click
Select metric. And as you can see here, this is what our map looks like at the
moment. So we're going to say if the threshold goes over $10, we'll say it's greater
than or equal to. And as you can see, it adds this little red bar up here, which is
the alarm state for this particular alarm. At the moment, the estimated charge it is
is going to be $1.85. So it's nowhere close to that $10 mark. If we wanted it to be a
little bit more granular, we could set it to 5, which gets it a little bit closer to what
the line would be. So then we would hit Next. So here's where you would add up
to an SNS topic, specifically so you would get an email if it goes into alarm from
having reached that $5 limit. You can also add notifications for when the alarm
goes into OK status or if there's not enough data for it to make an alarm at all.
That can be considered an alarm state as well. You also have particular actions
you can take because of that alarm. You can add Auto Scaling groups. In other
words, if a particular instance reaches a utilization cap, in other words, it maxes
out its CPU or gets to the point where it's not responding as well as it should, you
can set a CloudWatch alarm to trigger. And once it goes into alarm, it can scale
out for you. So that way you don't have to actively monitor your Auto Scaling
group as much. So let's say that we wanted to do a specific EC2 instance metric.
I currently have one EC2 that is running at the moment. So what we're going to
need is the instance ID of the instance we're going to monitor. You can get that ID
from the EC2 section of the console. I've already gotten mine, so I'll go ahead and
copy that and paste it here inside the EC2 section for the metric. So this is going
to give us specific metrics for this particular EC2. So let's say that we had a CPU
utilization alarm for this EC2. As you can see by this little dot here, that's the CPU
kicking on with the EC2. And let's say it would reach 5, which isn't actually that
big of a deal, but in this instance, we'll keep it there. So, let's say besides auto
scaling, there are other options that we have for our EC2 if that EC2 went into
alarm state, in other words, if that CPU utilization got too high, there are options
for us to change this particular EC2. We can either terminate the instance, in
other words, if the instance is no longer responding, we can cut the instance off.
We can force it to reboot because sometimes it's just an OEM, or an out-of-
memory, error that's causing it to skyrocket in usage like that, or we can stop the
instance. Now stopping the instance is also something that can trigger things like
auto scaling rules and things like that. If you stop an instance, your auto scaling
rules kick in saying, hey, there are not as many healthy instances that
are available and create a new instance for you. So I hope that cleared some
things up when it came to alarms and their metrics. I'll be leaving a link to a
resource page through AWS on some of the more specifics about each of the
metrics and what they go into. Like you saw, there are a lot of different metrics
that are available for you to make your alarms off of. So realistically, it's just going
to be what you need for each of your individual situations and what resources
you really want to monitor. Let's get back to this slides so we can talk about some
reference points. I'll see you there. Welcome back. Let's go over what we touched
on in this lesson. First, we talked about what CloudWatch metrics are, as well as
why they're important. Then we jumped into the console to take a look at
what CloudWatch alarms actually look like. I hope this cleared some things up,
and I look forward to seeing you in the next one.
Exploring SNS
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be exploring SNS, specifically what exactly is it and how does it work? After we
touch on those two things, we're going to jump into the console and take a look
at it in real time. Let's get started. Okay, so first things first. What exactly does
SNS stand for? SNS stands for Simple Notification Service, and it is the way that
you're going to communicate outside of your account. Because what SNS is an
app to person or app-to-app notification setting. So, think like you have a
CloudWatch alarm and that alarm goes off. Well, you want to know when that
alarm would go off. And by making an SNS topic, you can assign it to that
CloudWatch alarm, so that way it will send out an email, or if you have it set up
correctly, even a phone call to you, or even let other applications know, hey, this
is happening, and we need to address it. The other thing that's specific about
SNS is it's event-driven. So you can set an SNS topic to specifically go off of an
event that's happening inside of your account. So anything from something as
simple as, hey, we need to scale out because we're having a high traffic load can
be attached to an SNS topic. And if you are subscribed to that topic, either with
your email or phone number or if it's sent to other applications, you can get
notified that hey, there was a scaling event that happened inside of your
account, which can be very useful for things like making sure your account stays
healthy in the long run. But let's go into some more nitty gritty. So when you're
using SNS, you can increase your security flow. It allows you to have encrypted
communications or private links, so that way you can have a specific interaction
that's happening just between you and whatever the event is happening in your
account. This can be really useful if you have specifically sensitive data or if you
don't particularly want other people to realize what's happening inside of your
account. Another good thing about SNS is you can decrease your costs with this
particular service. SNS allows you to simplify your infrastructure when it comes to
things like sending out messages. You don't have to pay for other services
because it includes things like filtering, batch deliveries, even its own setup
subscriber systems. All of that is incorporated into the SNS service. You also have
increased your ability for your messages. Because of the fact that your messages
can be stored in multiple data centers and can have multiple retry attempts at
delivery, that means that there's a very good possibility that even if the worst
were to happen and we were to lose the entire data center, your messages would
still be protected. The last thing that I want to bring up is the increased accuracy
you have with SNS compared to some other messaging services. Amazon has a
first in, first out section specifically for topics and queues, which means things
like message duplication and message lost, its really, really reduced in those
types of queues, which can be really useful in the long run for a lot of different
environments. Okay, so now that we've touched specifically on what SNS is and
what it can do, let's take a look in the console and see what it looks like from
there. And welcome to the AWS console. In the console today, we're going to be
talking about how to add an SNS topic to a CloudWatch alarm. So first things first
was we need to create the SNS topic. If you don't have it on your Recently visited
or under your bookmark bar, the easiest way to find it would be going up to
Search, type in SNS, click on SNS, and create a new topic. Our new topic is going
to be called Alamr, oops, spelled correctly, Alarm. Next up, we're going to do a
Standard. This is going to be a best-effort alarm, which is useful for what we're
trying to do. We're going to do the Display name of my topic. Nothing else really is
actively important here, though we can add encryptions or data protections if we
really needed to. But since we don't, we're going to Create topic, and our topic
was created. So what we're going to do next is create a subscription to our
topic. We're going to select the Protocol of Email. We're going to grab a
temporary email address, then Create subscription. Our subscription was
created. So if we go back to Alarm, we can see that it is currently Pending
confirmation. We have one inbox message. So in order to confirm our
subscription, we just click on this little Confirm button, and our subscription has
been confirmed. So we go back to our subscription here and rerefresh the
page, and we have a confirmation that it has been confirmed. So now we're going
to add this SNS topic to a CloudWatch alarm. So what we're going to do is we're
going to go to CloudWatch, and now we're going to click on this alarm here. We're
going to click Actions and Edit. So this alarm is for the status check of an EC2
instance. We're going to test this alarm by turning it off in just a moment. We're
going to click Next. Now we're going to go to notifications, and this goes into the
alarm state. We're going to have it send an email to the Alarm SNS topic. It's
emailing it to our temporary email address. Go to Update alarm. All right, so as
you can see, our state is currently OK. We're going to make this not OK or at least
no information available for this alarm. How we're going to do that is we're going
to go to EC2, go to Instances (running), click on this instance and Instance
state, Stop instance. Correct, Stop instance. Now this can take a minute for it to
actually stop. But once it does, we should get an alarm from this alarm
stating, hey, this instance isn't OK anymore. So I'll be back in just a moment once
we've done that. And as you can see, it is now an alarm, and we should be getting
an email in just a second about the fact that this state is In alarm. And as you can
see here, you've received this email because the CloudWatch data has entered
the ALARM state. And because of that, we were able to get an email from our SNS
topic. So with that, let's head back to the slides so we can take a look at what we
learned in this particular lesson. I'll see you there. All right, so let's have a quick
review on what we touched on in this particular lesson. In this lesson, we talked
about what exactly is SNS, how it works, and then we jumped into the console to
take a look at it in real time. I hope this cleared some things up, and I look forward
to seeing you in the next one.
Learning about CloudTrail Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over CloudTrail, what CloudTrail is, how it works, and why you might
use it. And then after we go over that, we're going to jump into the console to see
how it works in practice. Let's get started. Okay, so what is CloudTrail? CloudTrail
is a lot like the crew manager on a ship as in with CloudTrail, you can track the
movements of all of the users inside of your AWS account and see what different
environmental changes are happening within your account, things like a
termination of an instance or an upload of an S3 bucket. So, now that we've got
the gist of what CloudTrail is, let's talk about how it works. CloudTrail works by
sending out API calls to an event log called a trail. Each action within your
account sends a call, and if it's done by a user, it changes the ID of that particular
call to add the user ID into the trail. Realistically, there are two different types of
trails. There's the multi-region trail, which is a best practice as you're monitoring
all the regions, which can make trails slightly more complicated. But you know all
the goings on in all the different regions, which can be really important for
catching events that happen that you might not be watching for. And then you
have single-region trails, which can be easier to read, but it means you aren't
monitoring the other regions, which can leave holes inside your reports. So now
that we've talked about how it works, let's talk about why you should use
CloudTrail. Realistically, there are three main reasons why it's important
to incorporate CloudTrail into your environment. The first is security. With user
IDs in your trails, you can easily see who's doing what inside of your account. The
second reason would be notification. You can attach an SNS topic to your
CloudTrail so that every time a specific event happens, you can get an email or a
phone call. And then finally, CloudTrail makes your audits so much easier. With
your trails saved in S3, that means you can have a list of events in your
account, which can be really important if you have to report those events
to potentially a governmental body or a monitoring service. All right, it's demo
time. We're going to go look into the console on how to get to the CloudTrail side
of the console and what those trails can look like. I'll see you there. And welcome
back to the AWS console. So from the home page, we're going to be going over to
the CloudTrail section of the console. And if you don't see your CloudTrail section
in your Recently viewed section here, we can get there fairly easily from going up
to the search bar. So how we're going to do that is we're going to click into the
search bar. Type in CloudT. You see CloudTrail pops up. We're going to click on
CloudTrail, and here is the dashboard for CloudTrail. Now, we're going to go up to
Event history, and we can see here are the events for this particular account. So
as you can see here, there are quite a few different events that happen basically
all the time. So let's say that you want to look for something specific like a specific
resource type. What we would do is we click on Resource type. And then we get
this lovely pop-up of the resources that we can potentially search for within
CloudTrail. We, at this point, are going to search for EC2. We're going to click on
AWS::EC2::Instance. And as you can see, we have a list of everything that we've
done in this account when it comes to instances. So you can see if we click on
this section here that says TerminateInstances, we can see that I terminated
some instances, and here are the resource IDs of those instances. We have the
Event ID, the number that CloudTrail tracked it as and where exactly I deleted it
from. So since I deleted it from the console, it's saying AWS Internal. If you had
done it through the CLI or through an API call, it would be using your IP address
or wherever you did that call from as the source IP. Now here we have the Event
record, basically everything that happened in that particular event. So from here,
we can see the eventName was TerminateInstances. We have the items
terminated were these three instances. And then we could see the codes that
happened when they were shutting down from the previous state that they were
in was running, and that happened for all three of the instances. We can also see
from the principalId right here who exactly did the deletion. So this is what your
trail reports will look like if you're looking for something specific like this. You also
get these for when you're building out instances. So we're going to click on this
option here, and this is what it looks like when you build out an instance. So in
this particular trail, you can see I built out two instances using the example key
pair, and the default subnet, and a new security group. We see the principalId of
the event here, and then we have the actual event that happened later on in the
file. From this page, you can also get some other information specifically about
their pricing, as well as the specific documentation when it comes to
CloudTrail, which is always useful if you're trying to find something specific about
your environment. All right, let's head back to the slides and take a look at what
we learned in this lesson. And we're back. Let's take a quick look on what we
touched on this lesson. First, we talked about what CloudTrail is. Then we talked
about how it works and why you might use it. And finally, we jumped into the
console to take a look at CloudTrail in practice. I hope this cleared some things
up, and I look forward to seeing you in the next lesson.
Exploring the AWS Health Dashboard
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over the AWS Health Dashboard, what it is, how it works, as well as
jumping into the console to take a look at it from there. Let's get started. So, what
is the AWS Health Dashboard? The AWS Health Dashboard is a notification space,
which can be really useful for knowing the goings on in your specific
account. These notifications can be anything from an instance being retired
where the underlying hardware of your EC2 needs to be moved to a new host or
something as simple as you have an S3 bucket that needs to be updated. It also
allows you to personalize your view of your services that are currently employed
with AWS. So that way you can have a big-picture look of how AWS is working as
a whole, if you have any impacts or anything that is specific going on with a
particular service, so you can know how it's affecting your day-to-day
workload. Okay, so now that we've got a bit of a grasp on what the Health
Dashboard is, let's jump into the console and see what it looks like in practice. I'll
see you there. And welcome to the AWS console. So from the console, we're
going to go to the AWS Health Dashboard. There are a couple of different ways to
get there. Let's do the first one, which is clicking on this little bell icon, and it will
show you automatically if you have any specific things that need to be taken a
look at. Since we don't at the moment, they're all going to read 0. But the other
way you can get there is type in AWS health, and you'll get the AWS Health
Dashboard. Go ahead and click on that. And as you can see, at the moment, there
are no issues in the AWS system. Now in these particular cases, this is also where
you can see things like what the service history can look like. Let's say we wanted
to know what EC2 looked like over the last few days. We're going to click on
Service = EC2. We click on EC2, and as you can see, we get the Elastic Cloud
Compute in the various regions. And there hasn't been any issues for the last few
days, which, you know, really good. This can always be useful when it comes to
how you build out your system, and having your Health Dashboard for the
services that are actively important to you can be really helpful just for a really
quick jump in, check to see if anything's wrong, and then come right back out. It's
a very easy way to troubleshoot whether it's an issue on Amazon's side or if it's an
issue on your side if you're having issues with some of your services. Now under
Your account health, you'll also see other things here. You'll see Event log, Other
notifications, and Scheduled changes. So these are upgoing events that will
potentially happen in your account, things like you'll need to retire an
instance, which can look like this. Then, of course, you get your other
notifications. This can be things anywhere from billing notifications or rotating
your certificates or even just your vulnerabilities in your account. And then finally,
we have an event log, which shows you all of the recent events that
have happened inside of AWS as a whole. At the moment, as you can see, all of
them are showing as Closed, which is a really good thing. So let's head back to
the slides so we can take a look at what we learned in this lesson. And we're
back. Let's do a quick rundown on what we covered in this lesson. First, we talked
about the AWS Health Dashboard, as well as why you would use it. Then we
jumped into the console to take a look at how to get there and how to use the
dashboard. I hope this cleared some things up, and I look forward to seeing you in
the next one.
Reviewing Cost Explorer
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we'll be
talking about Cost Explorer, what it is, and why you might want to utilize it. Let's
get started. So first off, what exactly is Cost Explorer? The Cost Explorer is a way
to keep track of your current spend in your environment so you don't ever get a
surprise bill at the end of the month. Cost Explorer also allows you to keep track
of what you're forecasted to spend in the future for your environment. So that
way, you can make adjustments or changes, depending on what that forecast
sees. The benefits of Cost Explorer are actually twofold. The first thing, it allows
you to filter your findings and spend down to what's going on on a granular
level. You can also get customized reports so that you know what your spend is in
those different areas. All right, it's demo time. Let's take a look at the Cost
Explorer and the practice. I'll see you there. And welcome to the AWS console. In
the console today, we're going to be talking about the AWS Cost Explorer. We're
going to take a look at how monthly budgets work and set one of those up, so
let's get started. If you don't have Cost Explorer in your Recently visited
section, we can go ahead and go up to the search bar, type in Cost. And it should
pop up for you, AWS Cost Explorer. Go ahead and click on that. And this
theoretically is what your Cost Explorer home page should look like. Generally
speaking, you'll have this number be a little bit higher, as it's usually whatever
your cost is in this particular range. This particular account doesn't have any
active instances or anything like that on it, so its range is 0. We can go down to
Reports. And here are the monthly reports that you have available to you. They
vary depending on what's going on in your system. Let's go Monthly costs by
service. And as you can see, the service that costs the most is going to be
DynamoDB for this particular account with SNS, S3, and CloudWatch also being
there, but not nearly as intrinsic. So that's how we can get some of our explorer
information, as well as some of our breakdowns of what the total cost is, and it
breaks down what costs come from what particular areas. Now let's go over to
Budgets. Let's create a budget. As you can see, I currently have a monthly
budget of $20, and Thresholds is currently OK, but let's create another budget. So
we're going to create a Zero spend budget, and it's going to email our temporary
email address if it spends more than $0.01. We'll go ahead and create that
budget. When you reach over your monthly spend, in this case our zero-spend
budget, if you start spending any money, you'll get an email that looks something
like this that says, hey, just to let you know, you're going over your spend. This is
an alarm that's going off in your account. This can be really useful if you're a
student or somebody who really doesn't want to get a surprise bill from AWS
about their resources. And with that, it looks like we've covered everything that
we need to cover about Cost Explorer. Let's head back to the slides to see what
we touched on in this lesson. I'll see you there. And welcome back. Let's go over
what we touched on in this lesson. First, we talked about what Cost Explorer is
and why you might use it, then we jumped into the console to take a look at Cost
Explorer in practice. I hope this cleared some things up, and I look forward to
seeing you in the next one.
AWS Trusted Advisor
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about Trusted Advisor, what it is, how to use it, and then we'll jump
into the console and take a look at Trusted Advisor in practice. Let's get
started. So what exactly is AWS Trusted Advisor? Well, Trusted Advisor is your
friendly helper in your environment. The first thing it does is help you improve
your overall security inside your environment. It also is really good for regulatory
compliance, seeing as you can make sure that you're following exactly
what needs to be done inside of your environment. It's also good for optimization
for your environment. It provides tips and information on how to keep things
going as best as possible inside your environment. All right, it's demo time. Let's
jump into the console and take a look at what Trusted Advisor actually looks
like. I'll see you there. And welcome to the AWS console. In the console
today, we're going to be taking a look at the AWS Trusted Advisor and how it can
help you make sure your environment is safer than what it was before. If you don't
have it in your Recently visited or under your bookmark bar, the best way to find
it would be going up to the search bar, typing in Trusted, and it should pop up
Trusted Advisor. Click on Trusted Advisor, and give it a minute to load. Okay, so
here is the home page for the Trusted Advisor. For this account, you see there are
12 actions that are recommended, 21 that are recommended for investigation, and
nothing that's excluded at the moment with a potential savings of $16.07 a
month. You have recent changes that are down here of when things
happened. But let's go up to Security. So as you can see, there's a couple of
things here that are fairly straightforward. We get a better overview of our
security settings here. There are 10 things that have recommended actions, 18
things that require investigation, and 33 things that have no problems
detected. Okay, so let's show how this would change if we updated one of these
devices. So as you can see right here, we have an S3 Block Public Access setting
should be enabled on bucket-level. So that means that there's an S3 bucket that
has public access available in our system. So what we're going to do is we're
going to go up to Services, down to S3, open that in a new tab. All right, and we
see that there is a public bucket right here. So what we're going to do, so we're
going to click on that bucket. We have confirmed that there's no objects inside of
it. And since we're not using it at the moment, we're going to go ahead and delete
it. Copy the name of the bucket, paste it in there. And we have successfully
deleted the public access bucket. Now we go back to our compliance dashboard,
and now we refresh our checks. And with that, we see that we now only have 8
Action recommended items, 16 Investigation recommended, and 37 No problems
detected. So solving the problems will change it from having an
Action recommended to having No problems detected. You can also filter by
what type of check you're looking for. So let's say we want all the Trusted Advisor
stuff, and then we want the No problems detected. And with this information, we'll
be able to do things like fill out compliance reports since we already know what
we're doing inside of our environment to make it safer overall. Let's say for
regulatory compliance, we need to have things like CloudTrail logging
enabled, which we can confirm here. We also need to have IAM Password Policy
set up, which we can confirm right here. But let's say that you wanted to
download all of your checks just so you can be sure that you go through
everything on a weekly basis. What you can do is click on this button here and
click on Download all checks. And that will give you an Excel spreadsheet with all
of your checklists on there. You can use this checklist spreadsheet as a way to
inform any regulatory compliance reports if you have them. But let's say that we
were going to look at something else besides security. Let's say that we're going
to look at performance. So as you can see, in this account at the moment, there
are no Action recommended, no Investigations, and 13 No problems detected. So
that means that there aren't any updates AWS would recommend to make our
performance better in this account overall. If we head up to Cost optimization, we
have a potential monthly savings of $16.70, and that's because of this low
utilization of an Amazon EC2 instance. Since that particular instance is not
getting utilized, in other words, the CPU utilization was 10% or lower and network
I/O is 5 MB or less for 4 or more days, that means it's saying, hey, just to let you
know, it doesn't look like this particular EC2 instance is running very much. And
you can get which ones are which right in this particular section. Now, let's say
you wanted to know everything that's happening in your account on a weekly
basis. What you can do is you can go down to Notifications. You can add contacts
for billing, operations, and security to make it so that you once a week will receive
the Trusted Advisor recommendations. So that list that you see in Security,
Performance, Cost optimization, and Fault tolerance will be emailed out to the
specific contacts that you list. That can be really useful for keeping you up in
compliance, as well as keeping your environment nice and healthy. But let's say
that you really don't want to deal with Trusted Advisor. You can always turn
Trusted Advisor off with a simple flip of a switch and click the Disable button. This
makes it so that all the recommendations are turned off, and you don't have to
worry about Trusted Advisor clogging up your email. But we're going to turn it
back on. It can have useful insights. So with it enabled, we go back up to
Recommendations. And we see once again we have 10 things that need to be
looked at, 19 things that should be investigated, and 0 checks for excluded
items. Now you can exclude items from these checks, but I generally don't
recommend it. These checks are important and are utilized for keeping your
environment safe and healthy. But with that, you should have everything that you
need to get started with Trusted Advisor. Let's head back to the slides to see
what we touched on in this lesson. I'll see you there. And welcome back. Let's go
over what we touched on in this lesson. First, we talked about what Trusted
Advisor is, as well as why it's important to utilize it. Then we jumped into the
console to take a look at what Trusted Advisor actually looks like. I hope this
cleared some things up, and I'll see you in the next one.
Lambda Basics
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be talking about Lambda, both in theory and in practice. Let's get started. So
let's talk about Lambda. Lambda is a serverless offering that allows you to run
code without having to worry about underlying hardware. It's also event-driven,
so whenever something happens, it can trigger a lambda function to react to that
event. All right, it's demo time. Let's take a jump into the console to see
what lambda functions actually look like. I'll see you there. And welcome to the
AWS console. In the console today, we're going to be taking a look at Lambda and
how lambda functions work. So if you don't have Lambda on your Recently visited
or under your bookmark bar, the easiest way to get there is to go to the search
bar, type in Lambda, click on Lambda. We're going to create a new
function. Normally, you'll be put out at this dashboard page. We just got put in
the functions page since we have a function already in this account. Both from
the dashboard page or the function page, you can create a function by going to
Create function. Instead of going from scratch, we're going to use a blueprint for
this demo. So we're going to Use a blueprint. We're going to use the Hello world
function. We're going to type Helloworld. So this is where the code actually
sits. You can see the return is event.key1. So event and key1 equals value1. So it
will echo back whatever we put in that first key value. So let's go with Create
function. And it can take a minute for it to create the function. All right, so we're
going to test out this function. So we're going to change the value from key
value1 to Hello_World. Save. We also need to name our event, so we're going to
call it WorldEvent. We're going to Save, and our response is Hello_World. But
anything inside of that key will actually work, so we'll configure a test event
again. Instead of saying Hello_World, let's go with Lets go Gurus. Save. We're
going to test it again, and there we go. Our response, Let's go
Gurus. Congratulations, you did your first lambda function! You can now set up
an event like somebody logging in for the first time that'll trigger this code to
run automatically and send out to an SNS topic. And don't worry, we have a lab
specifically on this when it comes to building out your lambda functions, so you'll
get to get your hands dirty and a little bit more in depth on this particular
process. With that, let's head back to the slides to take a look at what we learned
in this lesson. I'll see you there. And welcome back. Let's go over what we
touched on in this lesson. First, we talked about what Lambda is in theory, then
we jumped into the console to take a look at lambda functions in practice. I hope
this cleared some things up, and I look forward to seeing you in the next one.
What We Covered: Management Tools
Hello, everybody, and welcome back to AWS Essentials. In this video, we're
going to briefly go over what we covered in this section. First, we did an overview
of what management tools are. Then we jumped into CloudWatch, both the
basics of CloudWatch and understanding what it is and then understanding how
CloudWatch metrics work and setting up alarms. We also covered SNS and how it
specifically works and integrates with CloudWatch as a whole. After that, we
jumped into CloudTrail and what that does. After CloudTrail, we talked about the
Health Dashboard and why it's important to check that dashboard. We also talked
about Cost Explorer and how you can keep track of your bill. Then we talked
about AWS Trusted Advisor and how it can help you make changes to your
environment to keep it more secure and more stable. After that, we talked about
Lambda and what it does. And finally, you have this video, which was a quick
review of this section. Thank you for watching, and I look forward to seeing you in
the next one.
Security Tools
An Overview of Security Tools
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be covering AWS Secrets Manager, as well as Amazon CloudFront, what they
are, and how we might utilize them. Let's get started. So, AWS Secrets Manager,
what exactly is it? The Secrets Manager is a service that allows you to encode
your secrets instead of hard coding things like passwords into your code for
things like databases. It also allows for fast and easy password rotations. So you
don't have to change your code, you just have to change the secret. Okay, so now
that we know a little bit more about Secrets Manager, let's talk about why you
might use it. First and foremost, it would improve your overall security as it's
never really a good idea to have your passwords coded anywhere, much less a
code that might get flushed to the public. The other reason is easy
integration. Secrets Manager allows you to easily incorporate your secrets, things
like passwords, over a lot of different applications. Now let's talk about Amazon
CloudFront. CloudFront is a service that helps you provide a more stable website
for your clients through things like edge locations to help response times
and content delivery networks, which help cache your content to help keep your
latency really low. So, let's talk about the benefits of CloudFront. First and
foremost, CloudFront, with the help of AWS Shield, really helps with DDoS
protection, DDoS standing for distribution denial-of-service attacks where people
will maliciously load your site with a network of computers to attempt to cause
your site to crash. CloudFront also allows for you to secure your content by
making sure it only serves your site to people and places you want to see it. All
right, let's do a quick wrap-up of what we covered in this lesson. First, we covered
what Secrets Manager is and why you might utilize it. Then we talked about
CloudFront and the benefits of implementing it on your websites. I hope that
cleared some things up, and I look forward to seeing you in the next one.
Utilizing GuardDuty
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over GuardDuty. First, we'll take a look at what GuardDuty is, and
then we'll take a look at why you might use it. Let's get started. So, let's talk about
GuardDuty. Much like the name implies, it's a guard for your account. It actively
monitors your account, checking for signs of odd activity or signs of malware or
malicious software. You also get incredibly detailed security reports that can tell
you accurately what your vulnerabilities are and how to remediate them. So, now
that we have an idea of what GuardDuty is, let's talk about why you might use
it. Realistically, you would gain a lot of insight into things like a compromization
problem, which can really mess up your environment if it's not caught quickly and
effectively. Also, those detailed security reports can make you clear
and transparent ideas of your environment, which are really important if you have
to report back to a reporting body or even just your customers. All right, so let's
talk about what we briefly touched on in this lesson. We talked about what
GuardDuty is and why you might use it. I hope that cleared some things up, and I
look forward to seeing you in the next one.
Understanding AWS Security Hub
Hello, everybody, and welcome back to AWS Essentials. In this lesson, we're going
to be going over AWS Security Hub, what it is, and why you might use it. Let's get
started. So AWS Security Hub is a security tool that specializes in making sure
that your account is always utilizing the best practices to make sure that it's
running safe, efficiently, and smoothly. And because of that, it means that you
can have a standardization across your account and your other AWS
environments. Okay, so what's some of the other reasons why you might use
Security Hub? Security Hub allows you to have customized reports and searches
that filter your service data to have information that you really need to see. It also
allows for smooth and easy integration into a whole lot of outside services that
can help inform support technicians and give them information right at their
fingertips. All right, let's do a quick wrap-up of what we touched on in this
video. First, we talked about what Security Hub is, and then we talked about why
you might use it. I hope this cleared some things up, and I look forward to seeing
you in the next one.
Conclusion
What We Covered in This Course
Hey there, Gurus. My name is Elizabeth Hord. Oh, one second. There we go. That's
better. Congratulations, Gurus! You made it through AWS Essentials. Let's do a
quick recap of what you learned in this course. First, we talked about the power
of an AWS account. Then we talked about IAM, or identity access management
and how that works. After that, we talked about EC2 and how to utilize them. Then
we jumped into S3 and all the storage solutions that are available for it. From
there, we jumped into VPCs and talked about how the networking inside of VPCs
works. Then we jumped into databases and how you can use a database to store
customer data. After that, we talked about CloudFormation and how that can
be used to build out your entire environment. After we talked about
CloudFormation, we jumped into management tools, and management tools was
all those little, tiny tools that can make a giant difference in your account. And
one of the last things we covered was security tools. We talked about some of the
things that keep your environment safe and what can keep your account from
getting hacked. And now we're in the conclusion. In the next video, I've got some
recommendations for where you can go next from here. But once again,
congratulations on making it through! I know this was a long one, but it's over
now. Take a nice deep breath in and out. And you did it. I look forward to seeing
you in the next lesson.
Where Do You Go from Here?
Hello, everybody, and welcome back to the final video of AWS Essentials. We
covered a lot in this series, everything from just starting your account to some of
the basic security tools that come with it. I hope you were able to figure out how
to make your account work and to do what you need it to do. So, congratulations!
You made it through. And that's really impressive, but I know you might be asking
yourself, what now? Well, good news. I have some suggestions. So realistically
speaking, my natural suggestion of where to go after this course would be to look
into some of our services like AWS's introduction to Polly or a deep dive into
Lambda. Courses like these will give you more in-depth theories on what exactly
these particular things do, which might be really helpful in your business
overall. Now if you're feeling really motivated, you could take our Solutions
Architect course, which can help you get one of the best certifications in the
business. I hope I was able to teach you something in this course. Thank you for
all of your attention and your time dedicated to it. And remember, Gurus, keep
being awesome!