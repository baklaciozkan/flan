wordsHeader="CustomerName, ContactName, Address, City, PostalCode, Country"
bb="Cardinal","Tom B.", "Erichsen","Skagen" ,"Stavanger","4006","Norway"


def createHsh word
	keySplit=word.split(",")
	combineHsh=Hash.new
	keySplit.map { |key| combineHsh["#{key}"] = "null" }
	return combineHsh
end

 sqlhsh=createHsh wordsHeader
p sqlhsh.to_h

def one_line_generate_query( hash )
	"INSERT INTO table (#{hash.keys.join(",")}) VALUES ('#{hash.values.join("', '")}')"
end

sqlSentence=one_line_generate_query sqlhsh.to_h


begin
	file = File.open("C:\Users\Lenovo\RubymineProjects\deneme1", "w")
	file.write sqlSentence
rescue IOError => e
	#some error occur, dir not writable etc.
ensure
	file.close unless file.nil?
end


{"customername"=>"null", " ContactName"=>"null", " Address"=>"null", " City"=>"null", " PostalCode"=>"null", " Country"=>"null"}
