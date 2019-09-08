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
# <a name="filestream-data"></a>FILESTREAM Verileri

FıLESTREAM depolama özniteliği bir varbinary (max) sütununda depolanan ikili (BLOB) veriler içindir. FıLESTREAM öncesinde, ikili verileri depolamak için özel işleme gerekir. Metin belgeleri, görüntüler ve videolar gibi yapılandırılmamış veriler genellikle veritabanının dışında depolanır ve yönetimi zorlaştırır.

> [!NOTE]
> SqlClient kullanarak FıLESTREAM verileriyle çalışmak için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.

Varbinary (max) sütununda FıLESTREAM özniteliğini belirtmek SQL Server, verileri veritabanı dosyası yerine yerel NTFS dosya sisteminde depolamasına neden olur. Ayrı olarak depolansa da, veritabanında depolanan varbinary (max) verileriyle çalışma için desteklenen aynı Transact-SQL deyimlerini kullanabilirsiniz.

## <a name="sqlclient-support-for-filestream"></a>FıLESTREAM için SqlClient desteği

SQL Server <xref:System.Data.SqlClient>için .NET Framework veri sağlayıcısı, <xref:System.Data.SqlTypes> ad alanında tanımlanan <xref:System.Data.SqlTypes.SqlFileStream> sınıfı kullanarak FILESTREAM verilerine okumayı ve yazmayı destekler. `SqlFileStream`, veri akışlarına okumak ve yazmak için yöntemler sağlayan sınıfındandevralır.<xref:System.IO.Stream> Akıştan okuma, akıştan bir bayt dizisi gibi veri yapısına veri aktarır. Yazma, verileri veri yapısından akışa aktarır.

### <a name="creating-the-sql-server-table"></a>SQL Server tablosu oluşturma

Aşağıdaki Transact-SQL deyimleri çalışanlar adlı bir tablo oluşturur ve bir veri satırı ekler. FıLESTREAM depolamayı etkinleştirdikten sonra, bu tabloyu izleyen kod örnekleriyle birlikte kullanabilirsiniz. SQL Server Books Online 'daki kaynakların bağlantıları bu konunun sonunda bulunur.

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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Örnek: FıLESTREAM verilerini okuma, üzerine yazma ve ekleme

Aşağıdaki örnek, bir FıLESTREAM 'ten verilerin nasıl okunacağını gösterir. Kod, `FileAccess` dosyanın mantıksal yolunu alır `Read` ve ' a ve `FileOptions` `SequentialScan`' yi olarak ayarlar. Kod daha sonra SqlFileStream 'den arabelleğe bayt olarak okur. Baytlar daha sonra konsol penceresine yazılır.

Örnek ayrıca, var olan tüm verilerin üzerine yazıldığı bir FıLESTREAM 'e nasıl veri yazılacağını gösterir. Kod, dosyanın mantıksal yolunu `SqlFileStream`alır ve ' a `Write` ve `FileOptions` `SequentialScan`' ı ' a `FileAccess` ayarlayarak öğesini oluşturur. Dosyadaki tüm veriler değiştirilerek öğesine `SqlFileStream`tek bir bayt yazılır.

Örnek ayrıca, dosyanın sonuna veri eklemek için Seek yöntemi kullanılarak bir FıLESTREAM 'e nasıl veri yazılacağını gösterir. Kod, dosyanın mantıksal yolunu `SqlFileStream`alır ve ' a `ReadWrite` ve `FileOptions` `SequentialScan`' ı ' a `FileAccess` ayarlayarak öğesini oluşturur. Kod, mevcut dosyaya tek bir bayt ekleyerek dosyanın sonuna gitmek için Seek yöntemini kullanır.

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

Diğer bir örnek için bkz. [nasıl yapılır ve ikili verileri bir dosya akışı sütununda getirme](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).

## <a name="resources-in-sql-server-books-online"></a>SQL Server Books Online 'daki kaynaklar

FıLESTREAM için tüm belgeler SQL Server Books Online 'daki aşağıdaki bölümlerde bulunur.

|Konu|Açıklama|
|-----------|-----------------|
|[FıLESTREAM (SQL Server)](/sql/relational-databases/blob/filestream-sql-server)|FıLESTREAM depolamanın ne zaman kullanılacağını ve SQL Server veritabanı altyapısını bir NTFS dosya sistemiyle nasıl tümleştirdiğini açıklar.|
|[FıLESTREAM verileri için Istemci uygulamaları oluşturma](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|FıLESTREAM verileriyle çalışmaya yönelik Windows API işlevlerini açıklar.|
|[FıLESTREAM ve diğer SQL Server özellikleri](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|SQL Server diğer özellikleriyle FıLESTREAM verilerinin kullanılmasına ilişkin önemli noktalar, yönergeler ve sınırlamalar sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](sql-server-data-types.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../retrieving-and-modifying-data.md)
- [Kod Erişimi Güvenliği ve ADO.NET](../code-access-security.md)
- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
