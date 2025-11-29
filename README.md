# Car Rental System (local)


1. Create a MongoDB Atlas cluster (https://www.mongodb.com/cloud/atlas) and get a connection string. Replace the password/DB name as needed.
2. Copy `.env.example` to `.env` and paste your `MONGODB_URI` and any other required values (JWT_SECRET, ADMIN_USER, ADMIN_PASS).
3. Start backend:
```bash
cd backend
npm install
npm run start
4. Windows / PowerShell notes
	 - If you see: "cannot be loaded because running scripts is disabled on this system" when running `npm`, you can either allow scripts for the current user or run the command directly using `npm.cmd`:
		 - To allow scripts for the current user without admin privileges:
			 ```powershell
			 Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
			 ```
		 - Or run the npm CLI wrapper directly:
			 ```powershell
			 npm.cmd -v
			 npm.cmd run dev
			 ```
		5. Image upload: The Add Car form now supports image upload as an alternative to entering an image URL. If you upload an image in the Admin Add/Edit form, the file is stored under `public/uploads` and the car's `image` field points to `/uploads/<filename>`. The server automatically creates the uploads directory.
		6. Bulk upload (CSV): Admins can upload a CSV file to add multiple cars at once via Admin Panel. The CSV must include columns such as `make,model,year,pricePerDay,image`. Use the CSV 'Upload' control in Admin Panel to upload a CSV. The server persists valid rows and returns a report with inserted count and per-row errors.