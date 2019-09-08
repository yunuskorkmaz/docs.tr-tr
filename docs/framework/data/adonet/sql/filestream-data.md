---
title: FILESTREAM Verileri
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 87bed5dd345c240cc00b2c36aa976ec53fe63b93
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794100"
---
# <a name="filestream-data"></a><span data-ttu-id="b22cf-102">FILESTREAM Verileri</span><span class="sxs-lookup"><span data-stu-id="b22cf-102">FILESTREAM Data</span></span>

<span data-ttu-id="b22cf-103">FıLESTREAM depolama özniteliği bir varbinary (max) sütununda depolanan ikili (BLOB) veriler içindir.</span><span class="sxs-lookup"><span data-stu-id="b22cf-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="b22cf-104">FıLESTREAM öncesinde, ikili verileri depolamak için özel işleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="b22cf-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="b22cf-105">Metin belgeleri, görüntüler ve videolar gibi yapılandırılmamış veriler genellikle veritabanının dışında depolanır ve yönetimi zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="b22cf-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="b22cf-106">SqlClient kullanarak FıLESTREAM verileriyle çalışmak için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b22cf-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="b22cf-107">Varbinary (max) sütununda FıLESTREAM özniteliğini belirtmek SQL Server, verileri veritabanı dosyası yerine yerel NTFS dosya sisteminde depolamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b22cf-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="b22cf-108">Ayrı olarak depolansa da, veritabanında depolanan varbinary (max) verileriyle çalışma için desteklenen aynı Transact-SQL deyimlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b22cf-108">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="b22cf-109">FıLESTREAM için SqlClient desteği</span><span class="sxs-lookup"><span data-stu-id="b22cf-109">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="b22cf-110">SQL Server <xref:System.Data.SqlClient>için .NET Framework veri sağlayıcısı, <xref:System.Data.SqlTypes> ad alanında tanımlanan <xref:System.Data.SqlTypes.SqlFileStream> sınıfı kullanarak FILESTREAM verilerine okumayı ve yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="b22cf-110">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="b22cf-111">`SqlFileStream`, veri akışlarına okumak ve yazmak için yöntemler sağlayan sınıfındandevralır.<xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="b22cf-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="b22cf-112">Akıştan okuma, akıştan bir bayt dizisi gibi veri yapısına veri aktarır.</span><span class="sxs-lookup"><span data-stu-id="b22cf-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="b22cf-113">Yazma, verileri veri yapısından akışa aktarır.</span><span class="sxs-lookup"><span data-stu-id="b22cf-113">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="b22cf-114">SQL Server tablosu oluşturma</span><span class="sxs-lookup"><span data-stu-id="b22cf-114">Creating the SQL Server Table</span></span>

<span data-ttu-id="b22cf-115">Aşağıdaki Transact-SQL deyimleri çalışanlar adlı bir tablo oluşturur ve bir veri satırı ekler.</span><span class="sxs-lookup"><span data-stu-id="b22cf-115">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="b22cf-116">FıLESTREAM depolamayı etkinleştirdikten sonra, bu tabloyu izleyen kod örnekleriyle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b22cf-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="b22cf-117">SQL Server Books Online 'daki kaynakların bağlantıları bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b22cf-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="b22cf-118">Örnek: FıLESTREAM verilerini okuma, üzerine yazma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="b22cf-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="b22cf-119">Aşağıdaki örnek, bir FıLESTREAM 'ten verilerin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b22cf-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="b22cf-120">Kod, `FileAccess` dosyanın mantıksal yolunu alır `Read` ve ' a ve `FileOptions` `SequentialScan`' yi olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b22cf-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="b22cf-121">Kod daha sonra SqlFileStream 'den arabelleğe bayt olarak okur.</span><span class="sxs-lookup"><span data-stu-id="b22cf-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="b22cf-122">Baytlar daha sonra konsol penceresine yazılır.</span><span class="sxs-lookup"><span data-stu-id="b22cf-122">The bytes are then written to the console window.</span></span>

<span data-ttu-id="b22cf-123">Örnek ayrıca, var olan tüm verilerin üzerine yazıldığı bir FıLESTREAM 'e nasıl veri yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b22cf-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="b22cf-124">Kod, dosyanın mantıksal yolunu `SqlFileStream`alır ve ' a `Write` ve `FileOptions` `SequentialScan`' ı ' a `FileAccess` ayarlayarak öğesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b22cf-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="b22cf-125">Dosyadaki tüm veriler değiştirilerek öğesine `SqlFileStream`tek bir bayt yazılır.</span><span class="sxs-lookup"><span data-stu-id="b22cf-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="b22cf-126">Örnek ayrıca, dosyanın sonuna veri eklemek için Seek yöntemi kullanılarak bir FıLESTREAM 'e nasıl veri yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b22cf-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="b22cf-127">Kod, dosyanın mantıksal yolunu `SqlFileStream`alır ve ' a `ReadWrite` ve `FileOptions` `SequentialScan`' ı ' a `FileAccess` ayarlayarak öğesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b22cf-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="b22cf-128">Kod, mevcut dosyaya tek bir bayt ekleyerek dosyanın sonuna gitmek için Seek yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b22cf-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

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

<span data-ttu-id="b22cf-129">Diğer bir örnek için bkz. [nasıl yapılır ve ikili verileri bir dosya akışı sütununda getirme](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="b22cf-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="b22cf-130">SQL Server Books Online 'daki kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b22cf-130">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="b22cf-131">FıLESTREAM için tüm belgeler SQL Server Books Online 'daki aşağıdaki bölümlerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b22cf-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="b22cf-132">Konu</span><span class="sxs-lookup"><span data-stu-id="b22cf-132">Topic</span></span>|<span data-ttu-id="b22cf-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b22cf-133">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="b22cf-134">FıLESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b22cf-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="b22cf-135">FıLESTREAM depolamanın ne zaman kullanılacağını ve SQL Server veritabanı altyapısını bir NTFS dosya sistemiyle nasıl tümleştirdiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b22cf-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="b22cf-136">FıLESTREAM verileri için Istemci uygulamaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b22cf-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="b22cf-137">FıLESTREAM verileriyle çalışmaya yönelik Windows API işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b22cf-137">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="b22cf-138">FıLESTREAM ve diğer SQL Server özellikleri</span><span class="sxs-lookup"><span data-stu-id="b22cf-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="b22cf-139">SQL Server diğer özellikleriyle FıLESTREAM verilerinin kullanılmasına ilişkin önemli noktalar, yönergeler ve sınırlamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b22cf-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b22cf-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b22cf-140">See also</span></span>

- [<span data-ttu-id="b22cf-141">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b22cf-141">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="b22cf-142">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b22cf-142">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="b22cf-143">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b22cf-143">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="b22cf-144">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="b22cf-144">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="b22cf-145">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b22cf-145">ADO.NET Overview</span></span>](../ado-net-overview.md)
