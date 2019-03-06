class Bootcamp
  def initialize(name, slogan, student_capacity)
    @name = name
    @slogan = slogan
    @student_capacity = student_capacity
    @teachers = []
    @students = []
    @grades = Hash.new { |hash, k| hash[k] = []} 
  end
  
  def name
    @name
  end

  def slogan
    @slogan
  end

  def students
    @students
  end

  def teachers
    @teachers
  end

  def hire(teacher)
    @teachers << teacher
  end

  def enroll(student)
    if @students.length < @student_capacity
        @students << student && true
    else
        return false
    end
  end

  def enrolled?(name)
    @students.include?(name)
  end
  
  def student_to_teacher_ratio
    @students.length / @teachers.length
  end

    def add_grade(name, grade)
      if enrolled?(name)
        @grades[name] << grade && true
      else
        return false
      end
    end

    def num_grades(student)
     @grades[student].count
    end

    def average_grade(student)
      
        if @grades[student].length == 0 || !enrolled?(student)
            return nil
        else
            return @grades[student].sum / @grades[student].length
        end
    end

end
