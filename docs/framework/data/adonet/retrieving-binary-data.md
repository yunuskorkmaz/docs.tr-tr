---
title: İkili Verileri Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 9acda6631e17031a81ba06d9530739a586fac7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794438"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="59010-102">İkili Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="59010-102">Retrieving Binary Data</span></span>
<span data-ttu-id="59010-103">Varsayılan olarak, **DataReader** tüm veri satırları kullanılabilir duruma geldiğinde, gelen verileri bir satır olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="59010-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="59010-104">İkili büyük nesneler (blob 'Lar), tek bir satırda yer alamaz ve gigabayt veri içerebildiğinden, farklı bir işleme ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="59010-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="59010-105">**Command. ExecuteReader** yönteminde, <xref:System.Data.CommandBehavior> **DataReader**'ın varsayılan davranışını değiştirmek için bağımsız değişken alan bir aşırı yükleme vardır.</span><span class="sxs-lookup"><span data-stu-id="59010-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="59010-106">DataReader 'ın varsayılan <xref:System.Data.CommandBehavior.SequentialAccess> davranışını değiştirmek için **ExecuteReader** yöntemine geçirebilirsiniz, bu sayede veri satırlarını yüklemek yerine verileri, alındıkları sıraya göre yükler.</span><span class="sxs-lookup"><span data-stu-id="59010-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="59010-107">Bu, Blobları veya diğer büyük veri yapılarını yüklemek için idealdir.</span><span class="sxs-lookup"><span data-stu-id="59010-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="59010-108">Bu davranışın veri kaynağınıza bağlı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="59010-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="59010-109">Örneğin, Microsoft Access 'ten bir BLOB döndürmek, yüklenmiş olan tüm BLOBUN, alındığı gibi ardışık olarak değil, belleğe yüklenmesini sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="59010-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="59010-110">**DataReader** 'ı **SequentialAccess**kullanacak şekilde ayarlarken, döndürülen alanlara erişmek için kullanılan diziyi dikkat etmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="59010-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="59010-111">Varsayılan olarak, tüm satırı kullanılabilir olduğu anda yükleyen **DataReader**'ın varsayılan davranışı, sonraki satır okunana kadar herhangi bir sırada döndürülen alanlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="59010-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="59010-112">Ancak, **SequentialAccess** kullanılırken, **DataReader** tarafından döndürülen alanlara sırayla erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59010-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="59010-113">Örneğin, sorgunuz üçüncü bir BLOB olan üç sütun döndürürse, üçüncü alandaki BLOB verilerine erişmeden önce birinci ve ikinci alanların değerlerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="59010-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="59010-114">Üçüncü alana ilk veya ikinci alanlardan önce eriştiğinizde, birinci ve ikinci alan değerleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="59010-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="59010-115">Bunun nedeni, **SequentialAccess** **DataReader** 'ı verileri sırayla döndürecek şekilde değiştirmiş ve **DataReader** 'ın ötesinde okurken veri kullanılamadığı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="59010-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="59010-116">BLOB alanındaki verilere erişirken, veri içeren bir diziyi dolduran **DataReader**'ın, **GetBytes** veya **GetChars** türünde erişimcileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="59010-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="59010-117">Ayrıca karakter verileri için **GetString** kullanabilirsiniz; Ancak.</span><span class="sxs-lookup"><span data-stu-id="59010-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="59010-118">sistem kaynaklarını korumak için bir BLOB değerinin tamamını tek bir dize değişkenine yüklemek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59010-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="59010-119">Bunun yerine, döndürülecek verilerin belirli bir arabellek boyutunu ve döndürülen verilerden okunacak ilk bayt veya karakter için bir başlangıç konumu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59010-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="59010-120">**GetBytes** ve **GetChars** , döndürülen bayt `long` veya karakter sayısını temsil eden bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="59010-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="59010-121">**GetBytes** veya **GetChars**'e null bir dizi geçirirseniz, döndürülen uzun değer, blobdaki toplam bayt veya karakter sayısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="59010-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="59010-122">İsteğe bağlı olarak dizideki bir dizini, okunan verilerin başlangıç konumu olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59010-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59010-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="59010-123">Example</span></span>  
 <span data-ttu-id="59010-124">Aşağıdaki örnek, Microsoft SQL Server içindeki **pubs** örnek VERITABANıNDAN yayımcı kimliğini ve logoyu döndürür.</span><span class="sxs-lookup"><span data-stu-id="59010-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="59010-125">Yayımcı kimliği (`pub_id`) bir karakter alanıdır ve logo bir blob olan görüntüdür.</span><span class="sxs-lookup"><span data-stu-id="59010-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="59010-126">**Logo** alanı bir bit eşlem olduğundan, örnek **GetBytes**kullanarak ikili veri döndürür.</span><span class="sxs-lookup"><span data-stu-id="59010-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="59010-127">Alanlara ardışık olarak erişilmesi gerektiğinden, amblem öncesinde geçerli veri satırı için yayımcı KIMLIĞINE erişildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="59010-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59010-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59010-128">See also</span></span>

- [<span data-ttu-id="59010-129">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="59010-129">SQL Server Binary and Large-Value Data</span></span>](./sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="59010-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="59010-130">ADO.NET Overview</span></span>](ado-net-overview.md)
