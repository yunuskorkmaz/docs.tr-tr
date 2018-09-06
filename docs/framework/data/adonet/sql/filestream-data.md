---
title: FILESTREAM verileri
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: eef03d171d288cb2bc62c3aaa477a95a5ce718c3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741094"
---
# <a name="filestream-data"></a><span data-ttu-id="ad7b3-102">FILESTREAM verileri</span><span class="sxs-lookup"><span data-stu-id="ad7b3-102">FILESTREAM Data</span></span>
<span data-ttu-id="ad7b3-103">FILESTREAM depolama alanı özniteliğe VARBINARY(max) sütunda depolanan ikili (BLOB) veri içindir.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="ad7b3-104">FILESTREAM önce özel işlem ikili verilerin depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="ad7b3-105">Metin belgeleri, görüntüler ve video gibi yapılandırılmamış verileri yönetmek zorlaştıran veritabanı haricinde, genellikle depolanır.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad7b3-106">.NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üzeri) SqlClient kullanarak FILESTREAM verilerle çalışmak için.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="ad7b3-107">FILESTREAM özniteliğine VARBINARY(max) sütun belirterek SQL Server'ın yerel NTFS dosya sistemi yerine veritabanı dosyasındaki verileri depolamak neden olur.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="ad7b3-108">Ayrı olarak depolanır, ancak aynı kullanabilirsiniz [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] deyimleri veritabanında depolanan VARBINARY(max) verilerle çalışmak için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="ad7b3-109">FILESTREAM için SqlClient desteği</span><span class="sxs-lookup"><span data-stu-id="ad7b3-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="ad7b3-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] SQL Server için veri sağlayıcısı <xref:System.Data.SqlClient>, FILESTREAM kullanarak veri yazma ve okuma destekler <xref:System.Data.SqlTypes.SqlFileStream> sınıfı içinde tanımlanan <xref:System.Data.SqlTypes> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="ad7b3-111">`SqlFileStream` devralınan <xref:System.IO.Stream> veri akışları için yazma ve okuma için yöntemler sağlar sınıfını.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="ad7b3-112">Bir akıştan okuma bayt dizisi gibi bir veri yapısı içine akıştan verileri aktarır.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="ad7b3-113">Yazma, verileri veri yapısından bir akışa aktarır.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-sql-server-table"></a><span data-ttu-id="ad7b3-114">SQL Server tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad7b3-114">Creating the SQL Server Table</span></span>  
 <span data-ttu-id="ad7b3-115">Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] deyimleri employees adlı bir tablo oluşturur ve bir veri satırı ekler.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="ad7b3-116">FILESTREAM depolama etkinleştirdikten sonra izleyen kod örnekleri ile birlikte bu tabloyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="ad7b3-117">SQL Server Books Online kaynaklarına bağlantılar, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>  
  
```  
CREATE TABLE employees  
(  
  EmployeeId INT  NOT NULL  PRIMARY KEY,  
  Photo VARBINARY(MAX) FILESTREAM  NULL,  
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL  
  UNIQUE DEFAULT NEWID()  
)  
GO  
Insert into employees  
Values(1, 0x00, default)  
GO  
```  
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="ad7b3-118">Örnek: Okuma, üzerine ve FILESTREAM veri ekleme</span><span class="sxs-lookup"><span data-stu-id="ad7b3-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="ad7b3-119">Aşağıdaki örnek, bir FILESTREAM verileri okumak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="ad7b3-120">Ayar dosyasının mantıksal yolu kodunu alır `FileAccess` için `Read` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ad7b3-121">Kodu daha sonra bayt arabelleğe SqlFileStream okur.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="ad7b3-122">Bayt, ardından konsol penceresinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="ad7b3-123">Örnek, ayrıca tüm mevcut veriler yazılır bir FILESTREAM için veri yazmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="ad7b3-124">Kod mantıksal dosyanın yolunu alır ve oluşturur `SqlFileStream`ayarını `FileAccess` için `Write` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ad7b3-125">Tek bir bayt yazılır `SqlFileStream`, dosyadaki tüm verileri değiştirme.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="ad7b3-126">Örnek ayrıca, dosyanın sonuna veri eklemek için arama yöntemi kullanılarak için bir FILESTREAM veri yazmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="ad7b3-127">Kod mantıksal dosyanın yolunu alır ve oluşturur `SqlFileStream`ayarını `FileAccess` için `ReadWrite` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ad7b3-128">Kod, bir tek baytlı varolan dosyaya ekleme dosyanın sonuna aramak için arama yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Data;  
using System.IO;  
  
namespace FileStreamTest  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");  
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for the file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Read the contents as bytes and write them to the console  
                            for (long index = 0; index < fileStream.Length; index++)  
                            {  
                                Console.WriteLine(fileStream.ReadByte());  
                            }  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file   
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Write a single byte to the file. This will  
                            // replace any data in the file.  
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Seek to the end of the file  
                            fileStream.Seek(0, SeekOrigin.End);  
  
                            // Append a single byte   
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
  
        }  
    }  
}
```  
  
 <span data-ttu-id="ad7b3-129">Başka bir örnek için bkz: [depolamak ve bir dosya akışı sütuna ikili verileri getirmek nasıl](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="ad7b3-129">For another sample, see [How to store and fetch binary data into a file stream column](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="ad7b3-130">SQL Server Çevrimiçi Kitapları'nda kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ad7b3-130">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="ad7b3-131">FILESTREAM için kapsamlı belgeler, aşağıdaki bölümlerde SQL Server Çevrimiçi Kitapları'nda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="ad7b3-132">Konu</span><span class="sxs-lookup"><span data-stu-id="ad7b3-132">Topic</span></span>|<span data-ttu-id="ad7b3-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad7b3-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ad7b3-134">[Tasarlama ve uygulama FILESTREAM depolama](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ad7b3-134">[Designing and Implementing FILESTREAM Storage](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span></span>|<span data-ttu-id="ad7b3-135">FILESTREAM belgeler ve ilgili konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-135">Provides links to FILESTREAM documentation and related topics.</span></span>|  
|<span data-ttu-id="ad7b3-136">[FILESTREAM genel bakış](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ad7b3-136">[FILESTREAM Overview](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span></span>|<span data-ttu-id="ad7b3-137">FILESTREAM depolama kullanmak ne zaman ve nasıl bir NTFS dosya sistemi ile SQL Server veritabanı altyapısı tümleştirildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-137">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|<span data-ttu-id="ad7b3-138">[FILESTREAM depolama ile çalışmaya başlama](https://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ad7b3-138">[Getting Started with FILESTREAM Storage](https://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span></span>|<span data-ttu-id="ad7b3-139">SQL Server örneği üzerinde FILESTREAM etkinleştirme, bir veritabanı ve saklı FILESTREAM verileri için bir tablo oluşturma ve FILESTREAM veri içeren satırları işlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-139">Describes how to enable FILESTREAM on an instance of SQL Server, how to create a database and a table to stored FILESTREAM data, and how to manipulate rows containing FILESTREAM data.</span></span>|  
|<span data-ttu-id="ad7b3-140">[FILESTREAM depolama istemci uygulamalarında kullanma](https://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ad7b3-140">[Using FILESTREAM Storage in Client Applications](https://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span></span>|<span data-ttu-id="ad7b3-141">FILESTREAM verileri ile çalışmak için Win32 API işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-141">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|[<span data-ttu-id="ad7b3-142">FILESTREAM ve diğer SQL Server özellikleri</span><span class="sxs-lookup"><span data-stu-id="ad7b3-142">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="ad7b3-143">Dikkat edilecek noktalar, yönergeleri ve sınırlamaları kullanarak SQL Server'ın diğer özelliklerle FILESTREAM verileri için sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-143">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad7b3-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad7b3-144">See Also</span></span>  
 [<span data-ttu-id="ad7b3-145">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ad7b3-145">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="ad7b3-146">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ad7b3-146">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ad7b3-147">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ad7b3-147">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="ad7b3-148">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="ad7b3-148">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="ad7b3-149">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="ad7b3-149">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
