# Application Testing & Usage Guide

## Quick Start

1. **Install Dependencies**
   ```bash
   pip install flask pandas joblib scikit-learn
   ```

2. **Run the Application**
   ```bash
   python app.py
   ```
   The app will start on `http://localhost:5000`

## Page-by-Page Walkthrough

### Home Page (`/`)
- Displays welcome message and overview
- Shows key features and benefits
- Link to start assessment

### Prediction Form (`/predict`)
- **14 Health Input Fields**:
  - MMSE Score (0-30)
  - ADL Score (0-10)
  - Functional Assessment (0-10)
  - Memory Complaints (Yes/No)
  - Behavioral Problems (Yes/No)
  - Family History of Alzheimer's (Yes/No)
  - Sleep Quality (0-10)
  - BMI (10-50)
  - HDL Cholesterol (0-100 mg/dL)
  - LDL Cholesterol (0-200 mg/dL)
  - Diabetes (Yes/No)
  - Hypertension (Yes/No)
  - Cardiovascular Disease (Yes/No)
  - Education Level (None/Primary/Secondary/Tertiary/Higher)

**Form Features**:
- Real-time validation (turns red/green based on value ranges)
- Loading indicator during submission
- Error messages with dismiss button
- All fields marked as required

### Result Page (`/result`)
**New Enhancements**:
- **Risk Score Visualization**: Circular gauge (0-100%)
  - Green for low risk (< 50%)
  - Red for high risk (> 50%)
- **Prediction Result**: Main assessment outcome
- **Health Recommendations**: Personalized suggestions
- **Input Summary**: All entered values displayed
- **Action Buttons**:
  - Print Result (Full page print)
  - View Recommendations (Link to detailed page)
- **Timestamp**: Shows exact assessment date/time

### Recommendations Page (`/recommendations`)
- Detailed health recommendations
- Lifestyle tips and guidelines

## API Endpoints

### Health Tips API
```
GET /api/health-tips
```

**Response**:
```json
{
  "exercise": "Exercise 30 minutes daily...",
  "diet": "Mediterranean diet rich in...",
  "sleep": "Maintain consistent sleep...",
  "cognitive": "Engage in mentally...",
  "social": "Stay socially connected...",
  "stress": "Practice meditation..."
}
```

## Testing Scenarios

### Test Case 1: Healthy Assessment
**Input**:
- MMSE: 28
- ADL: 9
- Functional Assessment: 9
- Memory Complaints: No
- Sleep Quality: 8
- BMI: 24
- No medical conditions
- Education: Tertiary

**Expected Output**: Low risk assessment

### Test Case 2: At-Risk Assessment
**Input**:
- MMSE: 18
- ADL: 5
- Functional Assessment: 5
- Memory Complaints: Yes
- Sleep Quality: 4
- BMI: 29
- Family History: Yes
- Behavioral Problems: Yes
- Diabetes: Yes
- Hypertension: Yes

**Expected Output**: Higher risk assessment

### Test Case 3: Validation Testing
- Leave a field empty → Error message
- Enter value outside range → Red border + validation
- Negative values → Rejection
- Non-numeric in number field → Error

## Features to Verify

✓ Form validation (client-side)
✓ Required field checking (server-side)
✓ Range validation for numeric fields
✓ Successful prediction execution
✓ Result display with risk score
✓ Print functionality
✓ Navigation between pages
✓ Mobile responsiveness
✓ Error message display
✓ Session management (data persistence)

## Troubleshooting

### Model Not Loading
- Ensure `model.pkl` exists in the app directory
- Check file permissions
- Verify the model file is not corrupted

### Prediction Failed
- Check all inputs are within valid ranges
- Verify model features match form fields
- Check console for error logs

### Styling Issues
- Clear browser cache (Ctrl+Shift+Del)
- Ensure Bootstrap CDN is accessible
- Check internet connection

### Sessions Not Persisting
- Enable cookies in browser
- Check browser console for errors
- Verify session secret key is set

## Performance Notes

- Form submission takes ~1-2 seconds
- Prediction calculation depends on model complexity
- Page load time ~1-2 seconds on normal connection
- Mobile optimization for screens < 768px

## Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | Latest | ✓ Supported |
| Firefox | Latest | ✓ Supported |
| Safari | Latest | ✓ Supported |
| Edge | Latest | ✓ Supported |
| Mobile | Latest | ✓ Supported |

## Security Considerations

- All inputs are validated server-side
- Session data is encrypted
- No sensitive data logged
- CSRF protection enabled
- Input sanitization in place

## Future Enhancement Ideas

1. Add user authentication
2. Store assessment history
3. Export results to PDF
4. Email report functionality
5. Add more health metrics
6. Machine learning model improvements
7. Add progress tracking
8. Social sharing features

## Support & Documentation

For issues or questions:
1. Check browser console (F12)
2. Review server logs
3. Verify all dependencies installed
4. Check file permissions
5. Ensure model.pkl exists

---

**Last Updated**: April 16, 2026
**Application Version**: 2.0 (Enhanced)
**Python**: 3.8+
**Flask**: Latest
