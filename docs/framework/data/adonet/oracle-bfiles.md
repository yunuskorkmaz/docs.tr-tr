---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 5bb9f7e67016cf4b1d467935fe302ab4a40edbfa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304473"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="97902-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="97902-102">Oracle BFILEs</span></span>
<span data-ttu-id="97902-103">Oracle için .NET Framework veri sağlayıcısı içerir <xref:System.Data.OracleClient.OracleBFile> Oracle ile çalışmak için kullanılan sınıfı <xref:System.Data.OracleClient.OracleType.BFile> veri türü.</span><span class="sxs-lookup"><span data-stu-id="97902-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="97902-104">Oracle **BDOSYA** veri türü olan Oracle **LOB** boyut sınırı 4 gigabayt ikili verilerle bir başvuru içeren veri türü.</span><span class="sxs-lookup"><span data-stu-id="97902-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="97902-105">Oracle **BDOSYA** diğer Oracle'dan farklı **LOB** veri türlerini içeren, veriler işletim sistemi yerine fiziksel bir dosya sunucusunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="97902-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="97902-106">Unutmayın **BDOSYA** veri türü veri salt okunur erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="97902-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="97902-107">Diğer özelliklerini bir **BDOSYA** ondan ayırt veri türü bir **LOB** olan BT'nin veri türü:</span><span class="sxs-lookup"><span data-stu-id="97902-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="97902-108">Yapılandırılmamış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="97902-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="97902-109">Sunucu tarafı parçalama destekler.</span><span class="sxs-lookup"><span data-stu-id="97902-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="97902-110">Kopyalama semantiği kullanan başvuru.</span><span class="sxs-lookup"><span data-stu-id="97902-110">Uses reference copy semantics.</span></span> <span data-ttu-id="97902-111">Örneğin, bir kopyalama işlemi gerçekleştirirseniz bir **BDOSYA**, yalnızca **BDOSYA** (aynı dosyaya bir başvuru) Bulucu kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="97902-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="97902-112">Dosyadaki dosya kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="97902-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="97902-113">**BDOSYA** veri türü, boyutu büyük LOB'lar başvurmak için kullanılması gerekir ve bu nedenle, veritabanında depolamak pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="97902-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="97902-114">Daha fazla istemci ve sunucu iletişimi ek yük dahil kullanırken bir **BDOSYA** veri türü ile karşılaştırıldığında **LOB** veri türü.</span><span class="sxs-lookup"><span data-stu-id="97902-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="97902-115">Erişmek için daha verimli bir **BDOSYA** yalnızca az miktarda veriniz almak gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="97902-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="97902-116">Tüm nesnesi elde etmeniz gerekiyorsa veritabanı yerleşik LOB'lar erişmek için daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="97902-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="97902-117">NULL olmayan her **OracleBFile** nesne, temel alınan fiziksel dosya konumunu tanımlayan iki varlık ile ilişkilendirilmiş:</span><span class="sxs-lookup"><span data-stu-id="97902-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="97902-118">Dosya sistemindeki bir dizin için bir veritabanı diğer adı olan bir Oracle dizin nesnesi ve</span><span class="sxs-lookup"><span data-stu-id="97902-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="97902-119">Dizin nesneyle ilişkili dizinde bulunan temel alınan fiziksel dosyanın dosya adı.</span><span class="sxs-lookup"><span data-stu-id="97902-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97902-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="97902-120">Example</span></span>  
 <span data-ttu-id="97902-121">Aşağıdaki C# örneği nasıl oluşturabileceğinizi gösteren bir **BDOSYA** bir Oracle tablo ve ardından bunu biçiminde alma bir **OracleBFile** nesne.</span><span class="sxs-lookup"><span data-stu-id="97902-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="97902-122">Örnek kullanarak gösterir <xref:System.Data.OracleClient.OracleDataReader> nesne ve **OracleBFile** **arama** ve **okuma** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="97902-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="97902-123">Bu örneği kullanmak için öncelikle adlı bir dizin oluşturmanız gerekir Not "c:\\\bfiles" ve "MyFile.jpg" Oracle sunucusunda adlı bir dosya.</span><span class="sxs-lookup"><span data-stu-id="97902-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97902-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97902-124">See also</span></span>

- [<span data-ttu-id="97902-125">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="97902-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="97902-126">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="97902-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
