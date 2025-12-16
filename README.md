🔐 Authentication: The Identity Engine

Forget the default Django user model. G-Blogs runs on a bespoke, production-hardened authentication system designed for modern security standards and seamless user onboarding.

✨ Core Features

Feature

Description

🚀 Email-First Identity

Legacy usernames are out. We extend AbstractUser to make Email the primary unique identifier for a smoother login experience.

🛡️ Fortified Security

Built-in CSRF protection, secure session management, and granular @login_required view protection to keep data locked down.

⚡ Instant Verification

Asynchronous SMTP integration (via SendGrid) dispatches real-time activation links to verify user authenticity immediately.

🔄 Secure Recovery

A complete "Forgot Password" workflow featuring time-sensitive, cryptographically secure reset tokens.

🌐 One-Click Social

Frictionless Google OAuth2 integration using django-allauth. Sign up in seconds.

🤖 Reactive Profiles

Smart Django Signals (post_save) automatically provision rich user profiles the instant a new account is created.

🛠️ Under the Hood

# Custom User Manager Logic
class MyUserManager(BaseUserManager):
    def create_user(self, email, password=None, **extra_fields):
        if not email:
            raise ValueError('The Email field must be set')
        email = self.normalize_email(email)
        user = self.model(email=email, **extra_fields)
        # ... logic continues ...
