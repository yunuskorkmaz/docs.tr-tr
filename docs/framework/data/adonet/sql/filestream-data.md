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
# <a name="filestream-data"></a>FILESTREAM verileri
FILESTREAM depolama varbinary(max) sütunda depolanan ikili (BLOB) veriler için özniteliğidir. FILESTREAM önce ikili veri depolama özel olarak işlenmesi gerekli. Metin belgeleri, görüntüler ve video gibi yapılandırılmamış veriler genellikle yönetmek zorlaşır veritabanı dışında depolanır.  
  
> [!NOTE]
>  .NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üstü) SqlClient kullanarak FILESTREAM verilerle çalışmak için.  
  
 Bir varbinary(max) sütunu FILESTREAM özniteliğine belirtme neden [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] yerel NTFS dosya sistemi yerine veritabanı dosyasında verileri depolamak için. Ayrı olarak depolanır, ancak aynı kullanabilirsiniz [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] deyimleri veritabanında depolanan varbinary(max) verilerle çalışmak için desteklenir.  
  
## <a name="sqlclient-support-for-filestream"></a>FILESTREAM SqlClient desteği  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] İçin veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, okuma ve yazma FILESTREAM verileri kullanarak için destekler <xref:System.Data.SqlTypes.SqlFileStream> tanımlanan sınıfı <xref:System.Data.SqlTypes> ad alanı. `SqlFileStream`öğesinden devralınan <xref:System.IO.Stream> okuma ve verileri akışlara yazma yöntemleri sağlayan sınıf. Bir akışından okuma bayt dizisi gibi bir veri yapıda akıştan veri aktarır. Yazma verileri veri yapısından bir akışa aktarır.  
  
### <a name="creating-the-includessnoversionincludesssnoversion-mdmd-table"></a>Oluşturma [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] tablosu  
 Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] deyimleri Çalışanlar adlı bir tablo oluşturur ve bir veri satırı ekler. FILESTREAM depolama etkinleştirdikten sonra bu tablo izleyin kod örnekleri ile birlikte kullanabilirsiniz. Kaynaklara bağlantılar [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online bu konunun sonunda yer.  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Örnek: Okuma, üzerine ve FILESTREAM veri ekleme  
 Aşağıdaki örnek, bir FILESTREAM verileri okumak gösterilmiştir. Kod dosyası ayarı mantıksal yolu alır `FileAccess` için `Read` ve `FileOptions` için `SequentialScan`. Kod bayt arabelleğe SqlFileStream sonra okur. Bayt sonra konsol penceresine yazılır.  
  
 Örnek ayrıca varolan tüm veriler yazılır bir FILESTREAM veri yazmak nasıl gösterir. Kod dosyasının mantıksal yolu alır ve oluşturur `SqlFileStream`, ayar `FileAccess` için `Write` ve `FileOptions` için `SequentialScan`. Tek bir baytı yazılır `SqlFileStream`, herhangi bir veri dosyasındaki değiştirme.  
  
 Örnek de dosyanın sonuna veri eklemek için arama yöntemini kullanarak bir FILESTREAM veri yazmak gösterilmiştir. Kod dosyasının mantıksal yolu alır ve oluşturur `SqlFileStream`, ayar `FileAccess` için `ReadWrite` ve `FileOptions` için `SequentialScan`. Kod, tek bir baytı varolan dosyanın sonuna ekleme dosyanın sonuna aramak için arama yöntemini kullanır.  
  
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
  
 Başka bir örnek için bkz: [nasıl depolanacağını ve bir dosya akışı sütuna ikili veri getirecek şekilde](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).  
  
## <a name="resources-in-includessnoversionincludesssnoversion-mdmd-books-online"></a>Kaynaklarında [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları  
 Tüm belgeler FILESTREAM için aşağıdaki bölümlerde bulunan [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Tasarlama ve uygulama FILESTREAM depolama](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)|FILESTREAM belgeler ve ilgili konulara bağlantılar sağlar.|  
|[FILESTREAM genel bakış](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)|FILESTREAM depolama kullanmak ne zaman ve nasıl bir NTFS dosya sistemi ile SQL Server veritabanı altyapısı tümleştirir açıklar.|  
|[FILESTREAM depolama ile çalışmaya başlama](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)|SQL Server örneği üzerinde FILESTREAM etkinleştirme, bir veritabanı ve saklı FILESTREAM verileri için bir tablo oluşturma ve nasıl FILESTREAM verileri içeren satırları yönetileceğini açıklar.|  
|[FILESTREAM depolama istemci uygulamalarında kullanma](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)|FILESTREAM verilerle çalışmak için Win32 API işlevleri açıklanmaktadır.|  
|[FILESTREAM ve diğer SQL Server özellikleri](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)|Dikkat edilecek noktalar, kuralları ve sınırlamaları FILESTREAM verileri SQL Server'ın diğer özellikleri kullanmak için sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Kod Erişimi Güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [SQL Server İkili ve Büyük Değerli Veriler](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
