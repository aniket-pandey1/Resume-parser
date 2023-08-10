def calculate_score(job_requirements, candidate_skills):
    
    match_count = sum(1 for word in job_requirements if word in candidate_skills)
    return match_count
def find_best_candidate(job_requirements, candidate_profiles):
    best_candidate = None
    best_score = 0

    for candidate in candidate_profiles:
        candidate_skills = candidate['skills']
        candidate_experience = candidate['experience']
        communication_skills = candidate['communication_skills']
        
        score = calculate_score(job_requirements, candidate_skills)
        
        # Adjust score based on experience
        score += candidate_experience
        
        # Adjust score based on communication skills
        if communication_skills == 'excellent':
            score += 2
        elif communication_skills == 'good':
            score += 1
        
        # Check if the current candidate has a higher score than the previous best candidate
        if score > best_score:
            best_candidate = candidate
            best_score = score

    return best_candidate
#printing best candidate for the job
def print_candidate(candidate):
    if candidate:
        print("Best candidate for the job:")
        print(f"Name: {candidate['name']}")
        print(f"Skills: {', '.join(candidate['skills'])}")
        print(f"Experience: {candidate['experience']} years")
        print(f"Communication Skills: {candidate['communication_skills']}")
    else:
        print("No suitable candidates found.")
def get_job_requirements():
    job_requirements = []
    while True:
        requirement = input("Enter a job requirement (or 'done' to finish): ")
        if requirement.lower() == 'done':
            break
        job_requirements.append(requirement.lower())
    return job_requirements
def main():
    # Get job requirements from the user
    print("Enter the job requirements:")
    job_requirements = get_job_requirements()

    # Define candidate profiles
    candidate_profiles = [
        {
            'name': 'Gitthal',
            'skills': ['GUI using Pyqt module', 'data handling', 'java'],
            'experience': 8,
            'communication_skills': 'excellent'
        },
        {
            'name': 'Tilli',
            'skills': ['python', 'machine learning', 'data visualization','java'],
            'experience': 4,
            'communication_skills': 'good'
        },
        {
            'name': 'Jatta',
            'skills': ['C++', 'machine learning', 'communication skills'],
            'experience': 1,
            'communication_skills': 'excellent'
        },
        {
            'name': 'Sumesh',
            'skills': ['Html', 'deep learning', 'communication skills'],
            'experience': 4,
            'communication_skills': 'better'
        },
        {
            'name': 'David',
            'skills': ['python', 'data visualization', 'communication skills','java'],
            'experience': 5,
            'communication_skills': 'better'
        },
         {
            'name': 'Shekhar',
            'skills': ['SQL', 'data handling', 'Html','java'],
            'experience': 4,
            'communication_skills': 'good'
        },
         {
            'name': 'Soumya',
            'skills': ['python', 'data visualization', 'communication skills','deep learning'],
            'experience': 9,
            'communication_skills': 'excellent'
        },
         {
            'name': 'Varun',
            'skills': ['GUI using Pyqt module', 'data analysis', 'communication skills','C'],
            'experience': 2,
            'communication_skills': 'better'
        },
         {
            'name': 'Mahesh',
            'skills': ['python', 'data analysis', 'C','C++'],
            'experience': 6,
            'communication_skills': 'good'
        },
         {
            'name': 'Vishakha',
            'skills': ['Html', 'data analysis', 'communication skills','C++'],
            'experience': 2,
            'communication_skills': 'better'
        }
        
    ]

    # Find the best candidate
    best_candidate = find_best_candidate(job_requirements, candidate_profiles)

    # Output the best candidate
    print_candidate(best_candidate)
if __name__ == "__main__":
    main()
