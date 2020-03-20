---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149446"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="605b5-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="605b5-102">Oracle BFILEs</span></span>
<span data-ttu-id="605b5-103">Oracle için .NET Framework Data <xref:System.Data.OracleClient.OracleBFile> Provider, Oracle <xref:System.Data.OracleClient.OracleType.BFile> veri türüyle çalışmak için kullanılan sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="605b5-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="605b5-104">Oracle **BFILE** veri türü, maksimum 4 gigabayt boyutuna sahip ikili verilere başvuru içeren bir Oracle **LOB** veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="605b5-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="605b5-105">Oracle **BFILE,** verilerinin sunucu yerine işletim sistemindeki fiziksel bir dosyada depolanması açısından diğer Oracle **LOB** veri türlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="605b5-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="605b5-106">**BFILE** veri türünün verilere salt okunur erişim sağladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="605b5-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="605b5-107">**Bir BFILE** veri türünün lob veri **LOB** türünden ayıran diğer özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="605b5-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="605b5-108">Yapılandırılmamış veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="605b5-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="605b5-109">Sunucu tarafı öbeklemi destekler.</span><span class="sxs-lookup"><span data-stu-id="605b5-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="605b5-110">Referans kopya semantik kullanır.</span><span class="sxs-lookup"><span data-stu-id="605b5-110">Uses reference copy semantics.</span></span> <span data-ttu-id="605b5-111">Örneğin, bir **BFILE**üzerinde bir kopyalama işlemi gerçekleştirirseniz, yalnızca **BFILE** bulucu (dosyaya başvurudur) kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="605b5-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="605b5-112">Dosyadaki veriler kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="605b5-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="605b5-113">**BFILE** veri türü boyutu büyük olan LOB'lara başvurmak için kullanılmalıdır ve bu nedenle veritabanında depolamak için pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="605b5-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="605b5-114">**LOB** veri türüyle karşılaştırıldığında bir **BFILE** veri türü kullanırken daha fazla istemci, sunucu ve iletişim yükü söz konusudur.</span><span class="sxs-lookup"><span data-stu-id="605b5-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="605b5-115">Yalnızca az miktarda veri almanız **gerekiyorsa, Bir BFILE'ye** erişmek daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="605b5-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="605b5-116">Nesnenin tamamını edinmeniz gerekiyorsa veritabanında yerleşik LOB'lara erişmek daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="605b5-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="605b5-117">NULL Olmayan **Her OracleBFile** nesnesi, temel fiziksel dosyanın konumunu tanımlayan iki varlıkla ilişkilidir:</span><span class="sxs-lookup"><span data-stu-id="605b5-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="605b5-118">Dosya sistemindeki bir dizin için bir veritabanı diğer adı olan bir Oracle DIRECTORY nesnesi ve</span><span class="sxs-lookup"><span data-stu-id="605b5-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="605b5-119">DIzin nesnesi ile ilişkili dizinde bulunan altta yatan fiziksel dosyanın dosya adı.</span><span class="sxs-lookup"><span data-stu-id="605b5-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="605b5-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="605b5-120">Example</span></span>  
 <span data-ttu-id="605b5-121">Aşağıdaki C# örneği, Oracle tablosunda nasıl bir **BFILE** oluşturabileceğinizi ve ardından **oracleBFile** nesnesi biçiminde nasıl alabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="605b5-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="605b5-122">Örnek, nesnenin <xref:System.Data.OracleClient.OracleDataReader> ve **OracleBFile** **Ara** ve **Oku** yöntemlerinin kullanılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="605b5-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="605b5-123">Bu örneği kullanmak için öncelikle Oracle sunucusunda "c:\\\bfiles" adlı bir dizin ve "MyFile.jpg" adlı dosya oluşturmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="605b5-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="605b5-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="605b5-124">See also</span></span>

- [<span data-ttu-id="605b5-125">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="605b5-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="605b5-126">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="605b5-126">ADO.NET Overview</span></span>](ado-net-overview.md)
