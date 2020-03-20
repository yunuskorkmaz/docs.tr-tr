---
title: İkili Verileri Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: c914a9b0780e2e87e177502b0f9faff0e7c4b617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149056"
---
# <a name="retrieving-binary-data"></a>İkili Verileri Alma
Varsayılan olarak, **DataReader** gelen verileri tüm veri satırı kullanılabilir olur olmaz satır olarak yükler. Ancak, ikili büyük nesneler (BLOB'lar) tek bir satırda bulunamayan gigabaytlarkadar veri içerebildiklerinden farklı tedaviye ihtiyaç duyarlar. **Command.ExecuteReader** **yöntemi, DataReader'ın**varsayılan <xref:System.Data.CommandBehavior> davranışını değiştirmek için bir bağımsız değişken alacak bir aşırı yüke sahiptir. **DataReader'ın** varsayılan davranışını değiştirmek için **ExecuteReader** yöntemine geçerek <xref:System.Data.CommandBehavior.SequentialAccess> veri satırlarını yüklemek yerine, veri satırlarını aldıktan sonra sırayla yükleyecek. Bu, BLOB'ları veya diğer büyük veri yapılarını yüklemek için idealdir. Bu davranışın veri kaynağınıza bağlı olabileceğini unutmayın. Örneğin, Microsoft Access'ten bir BLOB döndürülme, alındığı sırada sırayla değil, tüm BLOB'nin belleğe yüklenmesini yükler.  
  
 **DataReader'ı** **SequentialAccess'i**kullanacak şekilde ayarlarken, döndürülen alanlara erişme sırasının dikkate alınır. Kullanılabilir olur olmaz tüm satırı yükleyen **DataReader'ın**varsayılan davranışı, bir sonraki satır okunana kadar döndürülen alanlara erişmenizi sağlar. Ancak **SequentialAccess'i** kullanırken, **DataReader** tarafından sırayla döndürülen alanlara erişmeniz gerekir. Örneğin, sorgunuz üçüncü sütun olmak üzere üç sütun döndürürse, üçüncü alandaki BLOB verilerine erişmeden önce birinci ve ikinci alanların değerlerini döndürmeniz gerekir. Birinci veya ikinci alanlardan önce üçüncü alana erişirseniz, birinci ve ikinci alan değerleri artık kullanılamaz. Bunun nedeni, **SequentialAccess'in** Verileri sırayla döndürecek şekilde **Veri Okuyucu'yu** değiştirmiş olması ve **DataReader'ın** geçmişte okuması sonrasında verilerin kullanılamamasıdır.  
  
 BLOB alanındaki verilere erişirken, bir diziyi verilerle dolduran **DataReader'ın** **GetBytes** veya **GetChars** yazılı erişimcilerini kullanın. Karakter verileri için **GetString'i** de kullanabilirsiniz; Ancak. sistem kaynaklarını korumak için tüm BLOB değerini tek bir dize değişkenine yüklemek istemeyebilirsiniz. Bunun yerine döndürülecek belirli bir arabellek veri boyutu ve döndürülen verilerden okunacak ilk bayt veya karakter için bir başlangıç konumu belirtebilirsiniz. **GetBytes** ve **GetChars,** döndürülen bayt veya karakter sayısını temsil eden bir `long` değer döndürür. Boş bir diziyi **GetBytes** veya **GetChars'a**geçirirseniz, döndürülen uzun değer BLOB'daki toplam bayt veya karakter sayısı olacaktır. Okunan veriler için başlangıç konumu olarak dizideki bir diziyi isteğe bağlı olarak belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Microsoft SQL Server'daki **pub örnek** veritabanından yayımcı kimliğini ve logosunu döndürür. Publisher ID`pub_id`( ) bir karakter alanıdır ve logo bir BLOB olan bir görüntüdür. **Logo** alanı bir bit eşlemi olduğundan, örnek **GetBytes**kullanarak ikili veri döndürür. Alanlara sırayla erişilmesi gerektiğinden, logodan önceki geçerli veri satırı için yayımcı kimliğine erişilene dikkat edin.  
  
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
