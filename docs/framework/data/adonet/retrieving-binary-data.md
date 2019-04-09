---
title: İkili Verileri Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 068b84e8704b54e6aea148ec5fc5bf9f0c4cb958
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085980"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="1a732-102">İkili Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="1a732-102">Retrieving Binary Data</span></span>
<span data-ttu-id="1a732-103">Varsayılan olarak, **DataReader** satırın tamamını veri kullanılabilir hemen sonra gelen verileri bir satır olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="1a732-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="1a732-104">Tek bir satırda bulunan verileri gigabayt içerdiğinden ikili büyük nesne (BLOB) ancak farklı işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a732-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="1a732-105">**Command.ExecuteReader** has sürecek bir aşırı yükleme yöntemi bir <xref:System.Data.CommandBehavior> varsayılan davranışını değiştirmek için bağımsız değişken **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="1a732-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="1a732-106">Geçirebilirsiniz <xref:System.Data.CommandBehavior.SequentialAccess> için **ExecuteReader** varsayılan davranışını değiştirmek için yöntem **DataReader** böylece alınan veri satırı yükleme yerine, verileri sıralı olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1a732-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="1a732-107">Bu, BLOB veya diğer büyük veri yapılarını yüklemek için idealdir.</span><span class="sxs-lookup"><span data-stu-id="1a732-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="1a732-108">Bu davranış, veri kaynağında değişebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1a732-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="1a732-109">Örneğin, bir BLOB Microsoft Access'ten döndüren alınan belleğe yerine sıralı olarak yüklenen tüm BLOB yükler.</span><span class="sxs-lookup"><span data-stu-id="1a732-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="1a732-110">Ayarlarken **DataReader** kullanılacak **SequentialAccess**, döndürülen alanlarla erişim sırası dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1a732-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="1a732-111">Varsayılan davranışını **DataReader**, kullanılabilir duruma geldiği satırın tamamını yükleyen sonraki satırda okuma kadar herhangi bir sırada döndürülen alanlarına erişmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1a732-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="1a732-112">Kullanırken **SequentialAccess** tarafından döndürülen alanlarla erişmeniz gerekir ancak **DataReader** sırayla.</span><span class="sxs-lookup"><span data-stu-id="1a732-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="1a732-113">Örneğin, sorgunuz, üçüncü bir BLOB ise üç sütun döndürürse, üçüncü alanında BLOB verilere erişmeden önce birinci ve ikinci alanların değerlerini döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a732-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="1a732-114">Önce ilk veya ikinci alanlarını alan erişirseniz, birinci ve ikinci alan değerlerini artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a732-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="1a732-115">Bunun nedeni, **SequentialAccess** değiştirdi **DataReader** veri sırası ve veri döndürmek için kullanılabilir değil sonra **DataReader** okuma izni.</span><span class="sxs-lookup"><span data-stu-id="1a732-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="1a732-116">BLOB alandaki verileri erişirken **GetBytes** veya **GetChars** yazılan erişicilerini **DataReader**, verilerle bir dizi doldurun.</span><span class="sxs-lookup"><span data-stu-id="1a732-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="1a732-117">Ayrıca **GetString** karakter verileri; ancak.</span><span class="sxs-lookup"><span data-stu-id="1a732-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="1a732-118">Sistem kaynaklarını korumak için BLOB değerin tamamını tek bir dize değişkene yük istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a732-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="1a732-119">Bunun yerine döndürülecek veri ve ilk bayt veya karakter, döndürülen verileri okumak için bir başlangıç konumunu belirli bir arabellek boyutunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a732-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="1a732-120">**GetBytes** ve **GetChars** döndüreceği bir `long` döndürülen karakter veya bayt sayısını temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="1a732-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="1a732-121">Boş bir dize geçirirseniz **GetBytes** veya **GetChars**, uzun değeri döndürdü BLOB karakter veya bayt sayısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1a732-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="1a732-122">İsteğe bağlı olarak, okunan veriler için bir başlangıç konumu olarak dizide dizin belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a732-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a732-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a732-123">Example</span></span>  
 <span data-ttu-id="1a732-124">Aşağıdaki örnek bir yayımcı kimliği ve logosu döndürür **pubs** örnek veritabanını Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1a732-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="1a732-125">Yayımcı kimliği (`pub_id`) karakter alan ve bir BLOB da bir görüntü logosudur.</span><span class="sxs-lookup"><span data-stu-id="1a732-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="1a732-126">Çünkü **logosu** alan bir bit eşlem, ikili verileri kullanarak bir örnek döndürür **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="1a732-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="1a732-127">Sıralı olarak alanlarını erişilmesi için yayımcı kimliği geçerli logosu önce veri satırı için erişilebilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1a732-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a732-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a732-128">See also</span></span>

- [<span data-ttu-id="1a732-129">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="1a732-129">SQL Server Binary and Large-Value Data</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="1a732-130">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1a732-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
