---
description: 'Daha fazla bilgi edinin: Oracle BFILEs'
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: e1fda4ad4acb225dc9a70c92b2c4f2b1d61ab1d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672497"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="7c0b6-103">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="7c0b6-103">Oracle BFILEs</span></span>

<span data-ttu-id="7c0b6-104">Oracle için .NET Framework Veri Sağlayıcısı, <xref:System.Data.OracleClient.OracleBFile> Oracle veri türüyle çalışmak için kullanılan sınıfını içerir <xref:System.Data.OracleClient.OracleType.BFile> .</span><span class="sxs-lookup"><span data-stu-id="7c0b6-104">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="7c0b6-105">Oracle **bDosya** veri türü, en fazla 4 gigabayt boyutlu ikili verilere başvuru Içeren bir Oracle **lob** veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-105">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="7c0b6-106">Oracle **bDosya** , verileri sunucu yerine işletim sistemindeki fiziksel bir dosyada depolanan diğer Oracle **lob** veri türlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-106">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="7c0b6-107">**BDosya** veri türünün verilere salt okunurdur erişimi sağladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-107">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="7c0b6-108">**Bir bu veri türünün** bir **lob** veri türünden ayırt edilmesini sağlayan diğer özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c0b6-108">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="7c0b6-109">Yapılandırılmamış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-109">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="7c0b6-110">Sunucu tarafı parçalama destekler.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-110">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="7c0b6-111">Başvuru kopyalama semantiğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-111">Uses reference copy semantics.</span></span> <span data-ttu-id="7c0b6-112">Örneğin, bir **bDosya** üzerinde kopyalama işlemi gerçekleştirirseniz, yalnızca **bDosya** Konumlandırıcı (dosyanın bir başvurusu) kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-112">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="7c0b6-113">Dosyadaki veriler kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-113">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="7c0b6-114">**BDosya** veri türü,, boyutu büyük olan LOBs 'ye başvurmak için kullanılmalıdır ve bu nedenle veritabanında depolanması pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-114">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="7c0b6-115">**Lob** veri türü ile karşılaştırıldığında bir **bDosya** veri türü kullanılırken daha fazla istemci, sunucu ve iletişim yükü söz konusu olur.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-115">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="7c0b6-116">Yalnızca az miktarda veri edinmeniz gerekiyorsa, bir **bDosya** 'ya erişmek daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-116">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="7c0b6-117">Nesnenin tamamını edinmeniz gerekiyorsa, veritabanına yerleşik lob 'Ları erişmek daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-117">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="7c0b6-118">NULL olmayan her bir **Oraclebdosya** nesnesi, temel alınan fiziksel dosyanın konumunu tanımlayan iki varlıkla ilişkilendirilir:</span><span class="sxs-lookup"><span data-stu-id="7c0b6-118">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="7c0b6-119">Dosya sistemindeki bir dizin için veritabanı diğer adı olan Oracle DIZIN nesnesi ve</span><span class="sxs-lookup"><span data-stu-id="7c0b6-119">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="7c0b6-120">DIZIN nesnesiyle ilişkili dizinde bulunan, temel alınan fiziksel dosyanın dosya adı.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-120">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c0b6-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c0b6-121">Example</span></span>  

 <span data-ttu-id="7c0b6-122">Aşağıdaki C# örneği, bir Oracle tablosunda bir **bDosya** oluşturup bunu bir **oraclebdosya** nesnesi biçiminde nasıl alabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-122">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="7c0b6-123">Örnek, <xref:System.Data.OracleClient.OracleDataReader> nesnesinin ve **oraclebdosya** **Seek** ve **Read** yöntemlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-123">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="7c0b6-124">Bu örneği kullanmak için, önce Oracle sunucusunda "c: \\ \bfiles" adlı bir dizin ve "MyFile.jpg" adlı dosya oluşturmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-124">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c0b6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c0b6-125">See also</span></span>

- [<span data-ttu-id="7c0b6-126">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c0b6-126">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="7c0b6-127">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7c0b6-127">ADO.NET Overview</span></span>](ado-net-overview.md)
