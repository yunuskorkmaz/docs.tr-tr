---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: d43dfccd9735ce1ab822d7b14de2abaa0940c77b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166605"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="5aa84-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="5aa84-102">Oracle BFILEs</span></span>

<span data-ttu-id="5aa84-103">Oracle için .NET Framework Veri Sağlayıcısı, <xref:System.Data.OracleClient.OracleBFile> Oracle veri türüyle çalışmak için kullanılan sınıfını içerir <xref:System.Data.OracleClient.OracleType.BFile> .</span><span class="sxs-lookup"><span data-stu-id="5aa84-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="5aa84-104">Oracle **bDosya** veri türü, en fazla 4 gigabayt boyutlu ikili verilere başvuru Içeren bir Oracle **lob** veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="5aa84-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="5aa84-105">Oracle **bDosya** , verileri sunucu yerine işletim sistemindeki fiziksel bir dosyada depolanan diğer Oracle **lob** veri türlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5aa84-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="5aa84-106">**BDosya** veri türünün verilere salt okunurdur erişimi sağladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5aa84-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="5aa84-107">**Bir bu veri türünün** bir **lob** veri türünden ayırt edilmesini sağlayan diğer özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5aa84-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="5aa84-108">Yapılandırılmamış verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5aa84-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="5aa84-109">Sunucu tarafı parçalama destekler.</span><span class="sxs-lookup"><span data-stu-id="5aa84-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="5aa84-110">Başvuru kopyalama semantiğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5aa84-110">Uses reference copy semantics.</span></span> <span data-ttu-id="5aa84-111">Örneğin, bir **bDosya**üzerinde kopyalama işlemi gerçekleştirirseniz, yalnızca **bDosya** Konumlandırıcı (dosyanın bir başvurusu) kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="5aa84-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="5aa84-112">Dosyadaki veriler kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="5aa84-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="5aa84-113">**BDosya** veri türü,, boyutu büyük olan LOBs 'ye başvurmak için kullanılmalıdır ve bu nedenle veritabanında depolanması pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="5aa84-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="5aa84-114">**Lob** veri türü ile karşılaştırıldığında bir **bDosya** veri türü kullanılırken daha fazla istemci, sunucu ve iletişim yükü söz konusu olur.</span><span class="sxs-lookup"><span data-stu-id="5aa84-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="5aa84-115">Yalnızca az miktarda veri edinmeniz gerekiyorsa, bir **bDosya** 'ya erişmek daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="5aa84-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="5aa84-116">Nesnenin tamamını edinmeniz gerekiyorsa, veritabanına yerleşik lob 'Ları erişmek daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="5aa84-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="5aa84-117">NULL olmayan her bir **Oraclebdosya** nesnesi, temel alınan fiziksel dosyanın konumunu tanımlayan iki varlıkla ilişkilendirilir:</span><span class="sxs-lookup"><span data-stu-id="5aa84-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="5aa84-118">Dosya sistemindeki bir dizin için veritabanı diğer adı olan Oracle DIZIN nesnesi ve</span><span class="sxs-lookup"><span data-stu-id="5aa84-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="5aa84-119">DIZIN nesnesiyle ilişkili dizinde bulunan, temel alınan fiziksel dosyanın dosya adı.</span><span class="sxs-lookup"><span data-stu-id="5aa84-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aa84-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5aa84-120">Example</span></span>  

 <span data-ttu-id="5aa84-121">Aşağıdaki C# örneği, bir Oracle tablosunda bir **bDosya** oluşturup bunu bir **oraclebdosya** nesnesi biçiminde nasıl alabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aa84-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="5aa84-122">Örnek, <xref:System.Data.OracleClient.OracleDataReader> nesnesinin ve **oraclebdosya** **Seek** ve **Read** yöntemlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aa84-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="5aa84-123">Bu örneği kullanmak için, önce Oracle sunucusunda "c: \\ \bfiles" adlı bir dizin ve "MyFile.jpg" adlı dosya oluşturmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5aa84-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5aa84-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa84-124">See also</span></span>

- [<span data-ttu-id="5aa84-125">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5aa84-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="5aa84-126">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5aa84-126">ADO.NET Overview</span></span>](ado-net-overview.md)
