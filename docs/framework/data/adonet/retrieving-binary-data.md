---
title: İkili Verileri Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 068b84e8704b54e6aea148ec5fc5bf9f0c4cb958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664291"
---
# <a name="retrieving-binary-data"></a>İkili Verileri Alma
Varsayılan olarak, **DataReader** satırın tamamını veri kullanılabilir hemen sonra gelen verileri bir satır olarak yükler. Tek bir satırda bulunan verileri gigabayt içerdiğinden ikili büyük nesne (BLOB) ancak farklı işlenmesi gerekir. **Command.ExecuteReader** has sürecek bir aşırı yükleme yöntemi bir <xref:System.Data.CommandBehavior> varsayılan davranışını değiştirmek için bağımsız değişken **DataReader**. Geçirebilirsiniz <xref:System.Data.CommandBehavior.SequentialAccess> için **ExecuteReader** varsayılan davranışını değiştirmek için yöntem **DataReader** böylece alınan veri satırı yükleme yerine, verileri sıralı olarak yüklenir. Bu, BLOB veya diğer büyük veri yapılarını yüklemek için idealdir. Bu davranış, veri kaynağında değişebilir unutmayın. Örneğin, bir BLOB Microsoft Access'ten döndüren alınan belleğe yerine sıralı olarak yüklenen tüm BLOB yükler.  
  
 Ayarlarken **DataReader** kullanılacak **SequentialAccess**, döndürülen alanlarla erişim sırası dikkate almak önemlidir. Varsayılan davranışını **DataReader**, kullanılabilir duruma geldiği satırın tamamını yükleyen sonraki satırda okuma kadar herhangi bir sırada döndürülen alanlarına erişmek olanak tanır. Kullanırken **SequentialAccess** tarafından döndürülen alanlarla erişmeniz gerekir ancak **DataReader** sırayla. Örneğin, sorgunuz, üçüncü bir BLOB ise üç sütun döndürürse, üçüncü alanında BLOB verilere erişmeden önce birinci ve ikinci alanların değerlerini döndürmesi gerekir. Önce ilk veya ikinci alanlarını alan erişirseniz, birinci ve ikinci alan değerlerini artık kullanılamaz. Bunun nedeni, **SequentialAccess** değiştirdi **DataReader** veri sırası ve veri döndürmek için kullanılabilir değil sonra **DataReader** okuma izni.  
  
 BLOB alandaki verileri erişirken **GetBytes** veya **GetChars** yazılan erişicilerini **DataReader**, verilerle bir dizi doldurun. Ayrıca **GetString** karakter verileri; ancak. Sistem kaynaklarını korumak için BLOB değerin tamamını tek bir dize değişkene yük istemeyebilirsiniz. Bunun yerine döndürülecek veri ve ilk bayt veya karakter, döndürülen verileri okumak için bir başlangıç konumunu belirli bir arabellek boyutunu belirtebilirsiniz. **GetBytes** ve **GetChars** döndüreceği bir `long` döndürülen karakter veya bayt sayısını temsil eden bir değer. Boş bir dize geçirirseniz **GetBytes** veya **GetChars**, uzun değeri döndürdü BLOB karakter veya bayt sayısı olacaktır. İsteğe bağlı olarak, okunan veriler için bir başlangıç konumu olarak dizide dizin belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir yayımcı kimliği ve logosu döndürür **pubs** örnek veritabanını Microsoft SQL Server. Yayımcı kimliği (`pub_id`) karakter alan ve bir BLOB da bir görüntü logosudur. Çünkü **logosu** alan bir bit eşlem, ikili verileri kullanarak bir örnek döndürür **GetBytes**. Sıralı olarak alanlarını erişilmesi için yayımcı kimliği geçerli logosu önce veri satırı için erişilebilir dikkat edin.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server İkili ve Büyük Değerli Veriler](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
