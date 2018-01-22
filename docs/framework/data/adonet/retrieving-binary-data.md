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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f91f23906a6d52a66a3cf972fe5636926dba4112
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="e6b80-102">İkili veriler alınıyor</span><span class="sxs-lookup"><span data-stu-id="e6b80-102">Retrieving Binary Data</span></span>
<span data-ttu-id="e6b80-103">Varsayılan olarak, **DataReader** bütün bir veri satırının kullanılabilir olduğu anda gelen verileri bir satır olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="e6b80-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="e6b80-104">Tek bir satırda bulunan verileri gigabayt içerdiğinden ikili büyük nesneler (BLOB) ancak, farklı işleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6b80-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="e6b80-105">**Command.ExecuteReader** yöntemi sürer bir aşırı sahip bir <xref:System.Data.CommandBehavior> varsayılan davranışını değiştirmek için bağımsız değişken **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="e6b80-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="e6b80-106">Geçirebilirsiniz <xref:System.Data.CommandBehavior.SequentialAccess> için **ExecuteReader** varsayılan davranışını değiştirmek için yöntemi **DataReader** böylece alındığında veri satırı yükleme yerine, verileri sıralı olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="e6b80-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="e6b80-107">Bu, BLOB veya diğer büyük veri yapılarını yüklemek için idealdir.</span><span class="sxs-lookup"><span data-stu-id="e6b80-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="e6b80-108">Bu davranış, veri kaynağında değişebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e6b80-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="e6b80-109">Örneğin, bir BLOB Microsoft Access'ten döndürme alındığında belleğe yerine sıralı olarak yüklenen tüm BLOB yükler.</span><span class="sxs-lookup"><span data-stu-id="e6b80-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="e6b80-110">Ayarlarken **DataReader** kullanmak için **SequentialAccess**, döndürülen alanları erişim sırası dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e6b80-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="e6b80-111">Varsayılan davranışını **DataReader**, kullanılabilir olduğunda hemen tüm satırı yükleyen erişim sonraki satıra okuma kadar herhangi bir sırada döndürülen alanlar olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e6b80-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="e6b80-112">Kullanırken **SequentialAccess** tarafından döndürülen alanları ancak erişmelisiniz **DataReader** sırayla.</span><span class="sxs-lookup"><span data-stu-id="e6b80-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="e6b80-113">Örneğin, sorgunuzu BLOB üçüncü biri olan üç sütun döndürürse, üçüncü alanında BLOB verilere erişmeden önce ilk ve ikinci alanlarına ait değerlerin döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6b80-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="e6b80-114">Birinci veya ikinci alanları önce üçüncü alanı erişirse, birinci ve ikinci alan değerlerini artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e6b80-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="e6b80-115">Bunun nedeni, **SequentialAccess** değiştirdi **DataReader** veri sırası ve veri döndürmek için kullanılabilir değil sonra **DataReader** okumak.</span><span class="sxs-lookup"><span data-stu-id="e6b80-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="e6b80-116">BLOB alandaki veri erişirken **GetBytes** veya **GetChars** yazılan erişimciler, **DataReader**, verilerle bir dizi doldurun.</span><span class="sxs-lookup"><span data-stu-id="e6b80-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="e6b80-117">Aynı zamanda **GetString** karakter veri; ancak.</span><span class="sxs-lookup"><span data-stu-id="e6b80-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="e6b80-118">Sistem kaynaklarını korumak için tek bir dize değişkeni BLOB değerin tamamını yük istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6b80-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="e6b80-119">Bunun yerine döndürülecek veri ve başlangıç konumu ilk bayta kalan veya karakteri döndürülen verileri okumak için belirli bir arabellek boyutunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6b80-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="e6b80-120">**GetBytes** ve **GetChars** döndürülecek bir `long` döndürülen karakterler veya bayt sayısını temsil eden değer.</span><span class="sxs-lookup"><span data-stu-id="e6b80-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="e6b80-121">Boş bir dizi geçirirseniz **GetBytes** veya **GetChars**, uzun değeri döndürülen bayt veya BLOB karakter sayısı toplam olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e6b80-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="e6b80-122">İsteğe bağlı olarak bir dizin dizideki okunan veriler için başlangıç konumu olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6b80-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b80-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6b80-123">Example</span></span>  
 <span data-ttu-id="e6b80-124">Aşağıdaki örnek yayımcı kimliği ve logosu döner **pubs** Microsoft SQL Server örnek veritabanında.</span><span class="sxs-lookup"><span data-stu-id="e6b80-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="e6b80-125">Yayımcı kimliği (`pub_id`) karakter alanı ve bir blobu bir görüntü logosu şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e6b80-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="e6b80-126">Çünkü **logosu** alan bir bit eşlem, ikili veriler kullanılarak örnek döndürür **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="e6b80-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="e6b80-127">Alanları sırayla erişilmesi için yayımcı kimliği logosu önce verilerin geçerli satır için erişilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e6b80-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6b80-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b80-128">See Also</span></span>  
 [<span data-ttu-id="e6b80-129">DataReader ile çalışma</span><span class="sxs-lookup"><span data-stu-id="e6b80-129">Working with DataReaders</span></span>](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="e6b80-130">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="e6b80-130">SQL Server Binary and Large-Value Data</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="e6b80-131">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="e6b80-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
