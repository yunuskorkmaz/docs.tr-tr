---
title: FILESTREAM Verileri
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 4edd03a38f8f5df6cb4fb9c2446f966dfe601564
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490070"
---
# <a name="filestream-data"></a><span data-ttu-id="caf37-102">FILESTREAM Verileri</span><span class="sxs-lookup"><span data-stu-id="caf37-102">FILESTREAM Data</span></span>

<span data-ttu-id="caf37-103">FILESTREAM depolama alanı özniteliğe VARBINARY(max) sütunda depolanan ikili (BLOB) veri içindir.</span><span class="sxs-lookup"><span data-stu-id="caf37-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="caf37-104">FILESTREAM önce özel işlem ikili verilerin depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="caf37-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="caf37-105">Metin belgeleri, görüntüler ve video gibi yapılandırılmamış verileri yönetmek zorlaştıran veritabanı haricinde, genellikle depolanır.</span><span class="sxs-lookup"><span data-stu-id="caf37-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="caf37-106">.NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üzeri) SqlClient kullanarak FILESTREAM verilerle çalışmak için.</span><span class="sxs-lookup"><span data-stu-id="caf37-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="caf37-107">FILESTREAM özniteliğine VARBINARY(max) sütun belirterek SQL Server'ın yerel NTFS dosya sistemi yerine veritabanı dosyasındaki verileri depolamak neden olur.</span><span class="sxs-lookup"><span data-stu-id="caf37-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="caf37-108">Ayrı olarak depolanan rağmen veritabanında depolanan VARBINARY(max) verilerle çalışmak için desteklenen aynı Transact-SQL deyimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caf37-108">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="caf37-109">FILESTREAM için SqlClient desteği</span><span class="sxs-lookup"><span data-stu-id="caf37-109">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="caf37-110">SQL Server için .NET Framework veri sağlayıcısı <xref:System.Data.SqlClient>, FILESTREAM kullanarak veri yazma ve okuma destekler <xref:System.Data.SqlTypes.SqlFileStream> sınıfı içinde tanımlanan <xref:System.Data.SqlTypes> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="caf37-110">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="caf37-111">`SqlFileStream` devralınan <xref:System.IO.Stream> veri akışları için yazma ve okuma için yöntemler sağlar sınıfını.</span><span class="sxs-lookup"><span data-stu-id="caf37-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="caf37-112">Bir akıştan okuma bayt dizisi gibi bir veri yapısı içine akıştan verileri aktarır.</span><span class="sxs-lookup"><span data-stu-id="caf37-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="caf37-113">Yazma, verileri veri yapısından bir akışa aktarır.</span><span class="sxs-lookup"><span data-stu-id="caf37-113">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="caf37-114">SQL Server tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="caf37-114">Creating the SQL Server Table</span></span>

<span data-ttu-id="caf37-115">Aşağıdaki Transact-SQL deyimlerini employees adlı bir tablo oluşturur ve bir veri satırı ekler.</span><span class="sxs-lookup"><span data-stu-id="caf37-115">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="caf37-116">FILESTREAM depolama etkinleştirdikten sonra izleyen kod örnekleri ile birlikte bu tabloyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="caf37-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="caf37-117">SQL Server Books Online kaynaklarına bağlantılar, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="caf37-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

```sql
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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="caf37-118">Örnek: Okuma, üzerine ve FILESTREAM veri ekleme</span><span class="sxs-lookup"><span data-stu-id="caf37-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="caf37-119">Aşağıdaki örnek, bir FILESTREAM verileri okumak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="caf37-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="caf37-120">Ayar dosyasının mantıksal yolu kodunu alır `FileAccess` için `Read` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="caf37-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="caf37-121">Kodu daha sonra bayt arabelleğe SqlFileStream okur.</span><span class="sxs-lookup"><span data-stu-id="caf37-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="caf37-122">Bayt, ardından konsol penceresinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="caf37-122">The bytes are then written to the console window.</span></span>

<span data-ttu-id="caf37-123">Örnek, ayrıca tüm mevcut veriler yazılır bir FILESTREAM için veri yazmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="caf37-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="caf37-124">Kod mantıksal dosyanın yolunu alır ve oluşturur `SqlFileStream`ayarını `FileAccess` için `Write` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="caf37-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="caf37-125">Tek bir bayt yazılır `SqlFileStream`, dosyadaki tüm verileri değiştirme.</span><span class="sxs-lookup"><span data-stu-id="caf37-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="caf37-126">Örnek ayrıca, dosyanın sonuna veri eklemek için arama yöntemi kullanılarak için bir FILESTREAM veri yazmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="caf37-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="caf37-127">Kod mantıksal dosyanın yolunu alır ve oluşturur `SqlFileStream`ayarını `FileAccess` için `ReadWrite` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="caf37-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="caf37-128">Kod, bir tek baytlı varolan dosyaya ekleme dosyanın sonuna aramak için arama yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="caf37-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

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
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
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

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
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

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
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

<span data-ttu-id="caf37-129">Başka bir örnek için bkz: [depolamak ve bir dosya akışı sütuna ikili verileri getirmek nasıl](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="caf37-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="caf37-130">SQL Server Çevrimiçi Kitapları'nda kaynaklar</span><span class="sxs-lookup"><span data-stu-id="caf37-130">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="caf37-131">FILESTREAM için kapsamlı belgeler, aşağıdaki bölümlerde SQL Server Çevrimiçi Kitapları'nda bulunur.</span><span class="sxs-lookup"><span data-stu-id="caf37-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="caf37-132">Konu</span><span class="sxs-lookup"><span data-stu-id="caf37-132">Topic</span></span>|<span data-ttu-id="caf37-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="caf37-133">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="caf37-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="caf37-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="caf37-135">FILESTREAM depolama kullanmak ne zaman ve nasıl bir NTFS dosya sistemi ile SQL Server veritabanı altyapısı tümleştirildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="caf37-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="caf37-136">FILESTREAM verileri için istemci uygulamalar oluşturun</span><span class="sxs-lookup"><span data-stu-id="caf37-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="caf37-137">FILESTREAM verileri ile çalışma için Windows API işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="caf37-137">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="caf37-138">FILESTREAM ve diğer SQL Server özellikleri</span><span class="sxs-lookup"><span data-stu-id="caf37-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="caf37-139">Dikkat edilecek noktalar, yönergeleri ve sınırlamaları kullanarak SQL Server'ın diğer özelliklerle FILESTREAM verileri için sağlar.</span><span class="sxs-lookup"><span data-stu-id="caf37-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="caf37-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caf37-140">See also</span></span>

- [<span data-ttu-id="caf37-141">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="caf37-141">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [<span data-ttu-id="caf37-142">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="caf37-142">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="caf37-143">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="caf37-143">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="caf37-144">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="caf37-144">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="caf37-145">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="caf37-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
