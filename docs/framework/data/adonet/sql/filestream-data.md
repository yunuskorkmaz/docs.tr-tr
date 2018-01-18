---
title: FILESTREAM verileri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 898fb6072742c745e7e86d2ea543803dc65ae014
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="filestream-data"></a><span data-ttu-id="02ee0-102">FILESTREAM verileri</span><span class="sxs-lookup"><span data-stu-id="02ee0-102">FILESTREAM Data</span></span>
<span data-ttu-id="02ee0-103">FILESTREAM depolama varbinary(max) sütunda depolanan ikili (BLOB) veriler için özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="02ee0-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="02ee0-104">FILESTREAM önce ikili veri depolama özel olarak işlenmesi gerekli.</span><span class="sxs-lookup"><span data-stu-id="02ee0-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="02ee0-105">Metin belgeleri, görüntüler ve video gibi yapılandırılmamış veriler genellikle yönetmek zorlaşır veritabanı dışında depolanır.</span><span class="sxs-lookup"><span data-stu-id="02ee0-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02ee0-106">.NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üstü) SqlClient kullanarak FILESTREAM verilerle çalışmak için.</span><span class="sxs-lookup"><span data-stu-id="02ee0-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="02ee0-107">Bir varbinary(max) sütunu FILESTREAM özniteliğine belirtme neden [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] yerel NTFS dosya sistemi yerine veritabanı dosyasında verileri depolamak için.</span><span class="sxs-lookup"><span data-stu-id="02ee0-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="02ee0-108">Ayrı olarak depolanır, ancak aynı kullanabilirsiniz [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] deyimleri veritabanında depolanan varbinary(max) verilerle çalışmak için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="02ee0-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="02ee0-109">FILESTREAM SqlClient desteği</span><span class="sxs-lookup"><span data-stu-id="02ee0-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="02ee0-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] İçin veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, okuma ve yazma FILESTREAM verileri kullanarak için destekler <xref:System.Data.SqlTypes.SqlFileStream> tanımlanan sınıfı <xref:System.Data.SqlTypes> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="02ee0-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="02ee0-111">`SqlFileStream`öğesinden devralınan <xref:System.IO.Stream> okuma ve verileri akışlara yazma yöntemleri sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="02ee0-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="02ee0-112">Bir akışından okuma bayt dizisi gibi bir veri yapıda akıştan veri aktarır.</span><span class="sxs-lookup"><span data-stu-id="02ee0-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="02ee0-113">Yazma verileri veri yapısından bir akışa aktarır.</span><span class="sxs-lookup"><span data-stu-id="02ee0-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-includessnoversionincludesssnoversion-mdmd-table"></a><span data-ttu-id="02ee0-114">Oluşturma [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] tablosu</span><span class="sxs-lookup"><span data-stu-id="02ee0-114">Creating the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Table</span></span>  
 <span data-ttu-id="02ee0-115">Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] deyimleri Çalışanlar adlı bir tablo oluşturur ve bir veri satırı ekler.</span><span class="sxs-lookup"><span data-stu-id="02ee0-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="02ee0-116">FILESTREAM depolama etkinleştirdikten sonra bu tablo izleyin kod örnekleri ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02ee0-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="02ee0-117">Kaynaklara bağlantılar [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online bu konunun sonunda yer.</span><span class="sxs-lookup"><span data-stu-id="02ee0-117">The links to resources in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online are located at the end of this topic.</span></span>  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="02ee0-118">Örnek: Okuma, üzerine ve FILESTREAM veri ekleme</span><span class="sxs-lookup"><span data-stu-id="02ee0-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="02ee0-119">Aşağıdaki örnek, bir FILESTREAM verileri okumak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="02ee0-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="02ee0-120">Kod dosyası ayarı mantıksal yolu alır `FileAccess` için `Read` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="02ee0-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="02ee0-121">Kod bayt arabelleğe SqlFileStream sonra okur.</span><span class="sxs-lookup"><span data-stu-id="02ee0-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="02ee0-122">Bayt sonra konsol penceresine yazılır.</span><span class="sxs-lookup"><span data-stu-id="02ee0-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="02ee0-123">Örnek ayrıca varolan tüm veriler yazılır bir FILESTREAM veri yazmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="02ee0-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="02ee0-124">Kod dosyasının mantıksal yolu alır ve oluşturur `SqlFileStream`, ayar `FileAccess` için `Write` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="02ee0-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="02ee0-125">Tek bir baytı yazılır `SqlFileStream`, herhangi bir veri dosyasındaki değiştirme.</span><span class="sxs-lookup"><span data-stu-id="02ee0-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="02ee0-126">Örnek de dosyanın sonuna veri eklemek için arama yöntemini kullanarak bir FILESTREAM veri yazmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="02ee0-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="02ee0-127">Kod dosyasının mantıksal yolu alır ve oluşturur `SqlFileStream`, ayar `FileAccess` için `ReadWrite` ve `FileOptions` için `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="02ee0-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="02ee0-128">Kod, tek bir baytı varolan dosyanın sonuna ekleme dosyanın sonuna aramak için arama yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="02ee0-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
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
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
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
} using (SqlConnection connection = new SqlConnection(  
    connStringBuilder.ToString()))  
{  
    connection.Open();  
  
    SqlCommand command = new SqlCommand("", connection);  
    command.CommandText = "select Top(1) Photo.PathName(), "  
    + "GET_FILESTREAM_TRANSACTION_CONTEXT () from employees";  
  
    SqlTransaction tran = connection.BeginTransaction(  
        System.Data.IsolationLevel.ReadCommitted);  
    command.Transaction = tran;  
  
    using (SqlDataReader reader = command.ExecuteReader())  
    {  
        while (reader.Read())  
        {  
            // Get the pointer for file  
            string path = reader.GetString(0);  
            byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
            FileStream fileStream = new SqlFileStream(path,  
                (byte[])reader.GetValue(1),  
                FileAccess.ReadWrite,  
                FileOptions.SequentialScan, 0);  
  
            // Seek to the end of the file  
            fs.Seek(0, SeekOrigin.End);  
  
            // Append a single byte   
            fileStream.WriteByte(0x01);  
            fileStream.Close();  
        }  
    }  
    tran.Commit();  
}  
```  
  
 <span data-ttu-id="02ee0-129">Başka bir örnek için bkz: [nasıl depolanacağını ve bir dosya akışı sütuna ikili veri getirecek şekilde](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="02ee0-129">For another sample, see [How to store and fetch binary data into a file stream column](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-includessnoversionincludesssnoversion-mdmd-books-online"></a><span data-ttu-id="02ee0-130">Kaynaklarında [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları</span><span class="sxs-lookup"><span data-stu-id="02ee0-130">Resources in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>  
 <span data-ttu-id="02ee0-131">Tüm belgeler FILESTREAM için aşağıdaki bölümlerde bulunan [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span><span class="sxs-lookup"><span data-stu-id="02ee0-131">The complete documentation for FILESTREAM is located in the following sections in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
|<span data-ttu-id="02ee0-132">Konu</span><span class="sxs-lookup"><span data-stu-id="02ee0-132">Topic</span></span>|<span data-ttu-id="02ee0-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02ee0-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02ee0-134">[Tasarlama ve uygulama FILESTREAM depolama](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="02ee0-134">[Designing and Implementing FILESTREAM Storage](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span></span>|<span data-ttu-id="02ee0-135">FILESTREAM belgeler ve ilgili konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="02ee0-135">Provides links to FILESTREAM documentation and related topics.</span></span>|  
|<span data-ttu-id="02ee0-136">[FILESTREAM genel bakış](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="02ee0-136">[FILESTREAM Overview](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span></span>|<span data-ttu-id="02ee0-137">FILESTREAM depolama kullanmak ne zaman ve nasıl bir NTFS dosya sistemi ile SQL Server veritabanı altyapısı tümleştirir açıklar.</span><span class="sxs-lookup"><span data-stu-id="02ee0-137">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|<span data-ttu-id="02ee0-138">[FILESTREAM depolama ile çalışmaya başlama](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="02ee0-138">[Getting Started with FILESTREAM Storage](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span></span>|<span data-ttu-id="02ee0-139">SQL Server örneği üzerinde FILESTREAM etkinleştirme, bir veritabanı ve saklı FILESTREAM verileri için bir tablo oluşturma ve nasıl FILESTREAM verileri içeren satırları yönetileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="02ee0-139">Describes how to enable FILESTREAM on an instance of SQL Server, how to create a database and a table to stored FILESTREAM data, and how to manipulate rows containing FILESTREAM data.</span></span>|  
|<span data-ttu-id="02ee0-140">[FILESTREAM depolama istemci uygulamalarında kullanma](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="02ee0-140">[Using FILESTREAM Storage in Client Applications](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span></span>|<span data-ttu-id="02ee0-141">FILESTREAM verilerle çalışmak için Win32 API işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02ee0-141">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|<span data-ttu-id="02ee0-142">[FILESTREAM ve diğer SQL Server özellikleri](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="02ee0-142">[FILESTREAM and Other SQL Server Features](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span></span>|<span data-ttu-id="02ee0-143">Dikkat edilecek noktalar, kuralları ve sınırlamaları FILESTREAM verileri SQL Server'ın diğer özellikleri kullanmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="02ee0-143">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02ee0-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02ee0-144">See Also</span></span>  
 [<span data-ttu-id="02ee0-145">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="02ee0-145">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="02ee0-146">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="02ee0-146">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="02ee0-147">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="02ee0-147">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="02ee0-148">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="02ee0-148">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="02ee0-149">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="02ee0-149">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
