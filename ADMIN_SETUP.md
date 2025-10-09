# Admin Setup

After DB is ready, create an admin user via SQL or register and update role.

Example SQL (run on your MySQL instance):

INSERT INTO users (phone, email, password_hash, name, role, referral_code) VALUES ('08000000000','admin@sauki.com','$2b$10$EXAMPLEHASH','Admin','admin','ADM001');

-- Or update existing user:
UPDATE users SET role='admin' WHERE phone='08000000000';

Default testing credentials:
- Phone: 08000000000
- Password: Sauki12345

(Generate a bcrypt hash for production.)
