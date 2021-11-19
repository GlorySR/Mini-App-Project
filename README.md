# Mini-App-Project
App Project (GameOfApps)

//full name error text view
<TextView
  android:id="@+id/fullNameErrorTextView"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:layout_marginHorizontal="16dp"
  android:text="Please enter your full name"
  android:textSize="12sp"
  android:fontFamily="@font/roboto"
  android:textColor="@color/orange_70"
  android:visibility="invisible" />

//email error text view
 <TextView
  android:id="@+id/emailAddressErrorTextView"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:layout_marginHorizontal="16dp"
  android:text="Please enter a valid email address"
  android:textSize="12sp"
  android:fontFamily="@font/roboto"
  android:textColor="@color/orange_70"
  android:visibility="invisible" />
  
//phone # error text view
<TextView
  android:id="@+id/phoneNumberErrorTextView"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:layout_marginHorizontal="16dp"
  android:text="Please enter a valid phone number"
  android:textSize="12sp"
  android:fontFamily="@font/roboto"
  android:textColor="@color/orange_70"
  android:visibility="invisible" />
  
//function to clear errors in signup screen (used in validateSignupEntries function)
private void clearSignUpScreenErrors() {
        EditText fullNameEditText = findViewById(R.id.fullNameEditText);
        fullNameEditText.setBackground(getDrawable(R.drawable.rounded_edittext));
        TextView fullNameErrorTextView = findViewById(R.id.fullNameErrorTextView);
        fullNameErrorTextView.setVisibility(View.GONE);
        EditText emailAddressEditText = findViewById(R.id.emailAddressEditText);
        emailAddressEditText.setBackground(getDrawable(R.drawable.rounded_edittext));
        TextView emailAddressErrorTextView = findViewById(R.id.emailAddressErrorTextView);
        emailAddressErrorTextView.setVisibility(View.GONE);
        EditText phoneNumberEditText = findViewById(R.id.phoneNumberEditText);
        phoneNumberEditText.setBackground(getDrawable(R.drawable.rounded_edittext));
        TextView phoneNumberErrorTextView = findViewById(R.id.phoneNumberErrorTextView);
        phoneNumberErrorTextView.setVisibility(View.GONE);
    }
  
// function to hide keyboard (used in validateSignupEntries Function)
private void hideKeyboard() {
        InputMethodManager imm = (InputMethodManager) getSystemService(Activity.INPUT_METHOD_SERVICE);
        //Find the currently focused view, so we can grab the correct window token from it.
        View view = getCurrentFocus();
        //If no view currently has focus, create a new one, just so we can grab a window token from it
        if (view == null) {
            view = new View(this);
        }
        imm.hideSoftInputFromWindow(view.getWindowToken(), 0);
        view.clearFocus();
    }
    
//  validateSignupEntries function (check input boxes for errors, returns error message) 
private boolean validateSignupEntries() {
        clearSignUpScreenErrors();
        boolean passedValidation = true; 

        EditText fullNameEditText = findViewById(R.id.fullNameEditText);
        TextView fullNameErrorTextView = findViewById(R.id.fullNameErrorTextView);
        String fullName = fullNameEditText.getText().toString();
        if (fullName.isEmpty()) {
            fullNameEditText.setBackground(getDrawable(R.drawable.rounded_orange_edittext));
            fullNameErrorTextView.setVisibility(TextView.VISIBLE);
            passedValidation = false;
        }

        EditText emailAddressEditText = findViewById(R.id.emailAddressEditText);
        TextView emailAddressErrorTextView = findViewById(R.id.emailAddressErrorTextView);
        String emailAddress = emailAddressEditText.getText().toString();
        if (emailAddress.isEmpty()) {
            emailAddressEditText.setBackground(getDrawable(R.drawable.rounded_orange_edittext));
            emailAddressErrorTextView.setVisibility(TextView.VISIBLE);
            passedValidation = false;
        }

        EditText phoneNumberEditText = findViewById(R.id.phoneNumberEditText);
        TextView phoneNumberErrorTextView = findViewById(R.id.phoneNumberErrorTextView);
        String phoneNumber = phoneNumberEditText.getText().toString();
        if (phoneNumber.isEmpty()) {
            phoneNumberEditText.setBackground(getDrawable(R.drawable.rounded_orange_edittext));
            phoneNumberErrorTextView.setVisibility(TextView.VISIBLE);
            passedValidation = false;
        }

        hideKeyboard();
        return passedValidation;
    }  
  
