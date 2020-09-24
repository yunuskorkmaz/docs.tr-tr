---
title: İkili Verileri Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 11f7a81bc0d4b0e2a8d66387410d9a24503c7519
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150667"
---
# <a name="retrieving-binary-data"></a>İkili Verileri Alma

Varsayılan olarak, **DataReader** tüm veri satırları kullanılabilir duruma geldiğinde, gelen verileri bir satır olarak yükler. İkili büyük nesneler (blob 'Lar), tek bir satırda yer alamaz ve gigabayt veri içerebildiğinden, farklı bir işleme ihtiyacı vardır. **Command.ExecuteReader** yöntemi, <xref:System.Data.CommandBehavior> **DataReader**'ın varsayılan davranışını değiştirmek için bağımsız değişken alacak bir aşırı yüklemeye sahiptir. <xref:System.Data.CommandBehavior.SequentialAccess> **DataReader** 'ın varsayılan davranışını değiştirmek için **ExecuteReader** yöntemine geçirebilirsiniz, bu sayede veri satırlarını yüklemek yerine verileri, alındıkları sıraya göre yükler. Bu, Blobları veya diğer büyük veri yapılarını yüklemek için idealdir. Bu davranışın veri kaynağınıza bağlı olabileceğini unutmayın. Örneğin, Microsoft Access 'ten bir BLOB döndürmek, yüklenmiş olan tüm BLOBUN, alındığı gibi ardışık olarak değil, belleğe yüklenmesini sağlayacaktır.  
  
 **DataReader** 'ı **SequentialAccess**kullanacak şekilde ayarlarken, döndürülen alanlara erişmek için kullanılan diziyi dikkat etmeniz önemlidir. Varsayılan olarak, tüm satırı kullanılabilir olduğu anda yükleyen **DataReader**'ın varsayılan davranışı, sonraki satır okunana kadar herhangi bir sırada döndürülen alanlara erişmenizi sağlar. Ancak, **SequentialAccess** kullanılırken, **DataReader** tarafından döndürülen alanlara sırayla erişmeniz gerekir. Örneğin, sorgunuz üçüncü bir BLOB olan üç sütun döndürürse, üçüncü alandaki BLOB verilerine erişmeden önce birinci ve ikinci alanların değerlerini döndürmelidir. Üçüncü alana ilk veya ikinci alanlardan önce eriştiğinizde, birinci ve ikinci alan değerleri artık kullanılamaz. Bunun nedeni, **SequentialAccess** **DataReader** 'ı verileri sırayla döndürecek şekilde değiştirmiş ve **DataReader** 'ın ötesinde okurken veri kullanılamadığı için geçerlidir.  
  
 BLOB alanındaki verilere erişirken, veri içeren bir diziyi dolduran **DataReader**'ın, **GetBytes** veya **GetChars** türünde erişimcileri kullanın. Ayrıca karakter verileri için **GetString** kullanabilirsiniz; Ancak. sistem kaynaklarını korumak için bir BLOB değerinin tamamını tek bir dize değişkenine yüklemek istemeyebilirsiniz. Bunun yerine, döndürülecek verilerin belirli bir arabellek boyutunu ve döndürülen verilerden okunacak ilk bayt veya karakter için bir başlangıç konumu belirtebilirsiniz. **GetBytes** ve **GetChars** , `long` döndürülen bayt veya karakter sayısını temsil eden bir değer döndürür. **GetBytes** veya **GetChars**'e null bir dizi geçirirseniz, döndürülen uzun değer, blobdaki toplam bayt veya karakter sayısı olacaktır. İsteğe bağlı olarak dizideki bir dizini, okunan verilerin başlangıç konumu olarak belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, Microsoft SQL Server içindeki **pubs** örnek VERITABANıNDAN yayımcı kimliğini ve logoyu döndürür. Yayımcı KIMLIĞI ( `pub_id` ) bir karakter alanıdır ve logo BIR blob olan görüntüdür. **Logo** alanı bir bit eşlem olduğundan, örnek **GetBytes**kullanarak ikili veri döndürür. Alanlara ardışık olarak erişilmesi gerektiğinden, amblem öncesinde geçerli veri satırı için yayımcı KIMLIĞINE erişildiğine dikkat edin.  
  
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

- [SQL Server İkili ve Büyük Değerli Veriler](./sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
