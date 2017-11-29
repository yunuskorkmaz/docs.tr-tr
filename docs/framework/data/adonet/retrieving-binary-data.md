---
title: "İkili veriler alınıyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd524ed605f1fe125480bae0949745f4f045f03a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-binary-data"></a>İkili veriler alınıyor
Varsayılan olarak, **DataReader** bütün bir veri satırının kullanılabilir olduğu anda gelen verileri bir satır olarak yükler. Tek bir satırda bulunan verileri gigabayt içerdiğinden ikili büyük nesneler (BLOB) ancak, farklı işleme gerekir. **Command.ExecuteReader** yöntemi sürer bir aşırı sahip bir <xref:System.Data.CommandBehavior> varsayılan davranışını değiştirmek için bağımsız değişken **DataReader**. Geçirebilirsiniz <xref:System.Data.CommandBehavior.SequentialAccess> için **ExecuteReader** varsayılan davranışını değiştirmek için yöntemi **DataReader** böylece alındığında veri satırı yükleme yerine, verileri sıralı olarak yükler. Bu, BLOB veya diğer büyük veri yapılarını yüklemek için idealdir. Bu davranış, veri kaynağında değişebilir unutmayın. Örneğin, bir BLOB Microsoft Access'ten döndürme alındığında belleğe yerine sıralı olarak yüklenen tüm BLOB yükler.  
  
 Ayarlarken **DataReader** kullanmak için **SequentialAccess**, döndürülen alanları erişim sırası dikkate almak önemlidir. Varsayılan davranışını **DataReader**, kullanılabilir olduğunda hemen tüm satırı yükleyen erişim sonraki satıra okuma kadar herhangi bir sırada döndürülen alanlar olanak tanır. Kullanırken **SequentialAccess** tarafından döndürülen alanları ancak erişmelisiniz **DataReader** sırayla. Örneğin, sorgunuzu BLOB üçüncü biri olan üç sütun döndürürse, üçüncü alanında BLOB verilere erişmeden önce ilk ve ikinci alanlarına ait değerlerin döndürmesi gerekir. Birinci veya ikinci alanları önce üçüncü alanı erişirse, birinci ve ikinci alan değerlerini artık kullanılamaz. Bunun nedeni, **SequentialAccess** değiştirdi **DataReader** veri sırası ve veri döndürmek için kullanılabilir değil sonra **DataReader** okumak.  
  
 BLOB alandaki veri erişirken **GetBytes** veya **GetChars** yazılan erişimciler, **DataReader**, verilerle bir dizi doldurun. Aynı zamanda **GetString** karakter veri; ancak. Sistem kaynaklarını korumak için tek bir dize değişkeni BLOB değerin tamamını yük istemeyebilirsiniz. Bunun yerine döndürülecek veri ve başlangıç konumu ilk bayta kalan veya karakteri döndürülen verileri okumak için belirli bir arabellek boyutunu belirtebilirsiniz. **GetBytes** ve **GetChars** döndürülecek bir `long` döndürülen karakterler veya bayt sayısını temsil eden değer. Boş bir dizi geçirirseniz **GetBytes** veya **GetChars**, uzun değeri döndürülen bayt veya BLOB karakter sayısı toplam olacaktır. İsteğe bağlı olarak bir dizin dizideki okunan veriler için başlangıç konumu olarak belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yayımcı kimliği ve logosu döner **pubs** Microsoft SQL Server örnek veritabanında. Yayımcı kimliği (`pub_id`) karakter alanı ve bir blobu bir görüntü logosu şeklindedir. Çünkü **logosu** alan bir bit eşlem, ikili veriler kullanılarak örnek döndürür **GetBytes**. Alanları sırayla erişilmesi için yayımcı kimliği logosu önce verilerin geçerli satır için erişilir dikkat edin.  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataReader ile çalışma](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [SQL Server ikili ve değeri büyük veri](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
