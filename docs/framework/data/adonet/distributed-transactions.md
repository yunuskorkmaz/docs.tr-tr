---
title: Dağıtılmış İşlemler
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: 89d94e94ea74c73a7f68f6052291c95a7c96f0d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150208"
---
# <a name="distributed-transactions"></a>Dağıtılmış İşlemler
Bir işlem (kaydetme) başarılı ya da başka şeylerin yanında bir birim olarak başarısız oluyor (iptal için) ilgili görevleri kümesidir. A *dağıtılmış işlem* çeşitli kaynaklar etkileyen bir işlemdir. İşlemek dağıtılmış işlem için tüm katılımcıları veri herhangi bir değişiklik kalıcı olmasını garanti gerekir. Sistem kilitlenme veya diğer öngörülemeyen olayları rağmen değişiklikleri kalıcı gerekir. Bu garanti yapmak tek bir katılımcı başarısız olursa, tüm işlemi başarısız olur ve işlem kapsamında değişiklikler geri alınır.  
  
> [!NOTE]
>  Tamamlama veya işlem durumunda geri denerseniz, bir özel durum bir `DataReader` işlem etkinken başlatılır.  
  
## <a name="working-with-systemtransactions"></a>System.Transactions ile çalışma  
 .NET Framework, dağıtılmış işlemler API üzerinden yönetilen <xref:System.Transactions> ad alanı. <xref:System.Transactions> API temsilci seçme dağıtılmış işlem birden çok kalıcı kaynak yöneticileri dahil olduğunda Microsoft Dağıtılmış İşlem Düzenleyicisi (MS DTC) gibi bir işlem İzleyicisi işleme. Daha fazla bilgi için [işlem Temelleri](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 ADO.NET 2.0 kullanarak bir dağıtılmış işlem kaydetme desteği sunmuştur `EnlistTransaction` bağlantı kaydeder yöntemi, bir <xref:System.Transactions.Transaction> örneği. ADO.NET önceki sürümlerini kullanarak dağıtılmış işlemler de açık kaydı gerçekleştirilmedi `EnlistDistributedTransaction` bağlantısının bağlantı listeleme yöntemi bir <xref:System.EnterpriseServices.ITransaction> örnek, hangi için geriye dönük uyumluluk desteklenir. Kurumsal Hizmetler işlemi hakkında daha fazla bilgi için bkz. [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Kullanırken bir <xref:System.Transactions> işlem .NET Framework sağlayıcısı ile SQL Server için basit bir SQL Server veritabanında <xref:System.Transactions.Transaction> otomatik olarak kullanılır. İşlem, bir tam dağıtılmış işlem gerektiğinde olarak sonra yükseltilebilir. Daha fazla bilgi için [SQL Server ile System.Transactions tümleştirmesi](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
>  Bir Oracle veritabanına aynı anda katılabilir dağıtılmış işlemlerin sayısı, varsayılan olarak 10'a ayarlanır. 10 işlem bir Oracle veritabanına bağlı bir özel durum oluşturulur. Oracle desteklemiyor `DDL` dağıtılmış bir işlem içinde.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Dağıtılmış bir işlem içinde otomatik olarak kaydetme  
 Otomatik kaydı, varsayılan (ve tercih edilen) ADO.NET bağlantıları ile tümleştirme yolu `System.Transactions`. Bir işlem etkin olduğunu belirlerse, bir bağlantı nesnesi otomatik olarak varolan bir dağıtılmış işlemde listeleme, içinde `System.Transaction` koşulları, yani `Transaction.Current` null değil. Bağlantı açıldığında otomatik bir işlem kaydı gerçekleşir. İşlem kapsamı içinde çalıştırılan bir komut olsa bile, daha sonra yapılmaz. Belirterek mevcut işlemlerde otomatik kayıt devre dışı bırakabilirsiniz `Enlist=false` için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>, veya `OLE DB Services=-7` için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Oracle ve ODBC bağlantı dizesi parametreleri hakkında daha fazla bilgi için bkz. <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> ve <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>El ile bir dağıtılmış işlemde kaydetme  
 Otomatik kayıt devre dışı bırakıldı veya bağlantı açıldıktan sonra başlatıldığı bir işleme kaydolunamadı ihtiyacınız varsa mevcut bir kullanarak dağıtılmış işlem listeleme `EnlistTransaction` yöntemi <xref:System.Data.Common.DbConnection> çalıştığınız sağlayıcısı nesnesi ile. Varolan bir dağıtılmış işlemde kaydetme hareket kaydedilmiş veya geri alınmış, veri kaynağındaki kod tarafından yapılan değişiklikleri kaydedilmiş veya geri yanı, sağlar.  
  
 Dağıtılmış işlemlerinde kaydetme iş nesneleri havuzu olduğunda özellikle geçerlidir. Bir iş nesnesi açık bir bağlantı ile bir havuzda toplanır, bu bağlantı açıldığında otomatik bir işlem kaydı yalnızca gerçekleşir. Birden çok işlem kullanarak havuza alınmış bir iş nesnesi gerçekleştirdiyseniz, bu nesne için açık bağlantı otomatik olarak yeni başlatılan işlemleri listeleme değil. Bu durumda, bağlantı için otomatik işlem kaydı devre dışı bırak ve bağlantı kullanarak işlem listeleme `EnlistTransaction`.  
  
 `EnlistTransaction` türünde tek bir bağımsız değişken <xref:System.Transactions.Transaction> mevcut işlem diğer bir deyişle bir başvuru. Bağlantının çağrıldıktan sonra `EnlistTransaction` yöntemi, veri kaynağı bağlantı işlemde dahil kullanarak yapılan tüm değişiklikleri. Bir null değeri geçirdiğini, geçerli bir dağıtılmış işlem kaydı bağlantısından unenlists. Çağırmadan önce bağlantıyı açılması gerektiğini unutmayın `EnlistTransaction`.  
  
> [!NOTE]
>  Bir bağlantı açıkça bir işlemde kayıtlı sonra ilk işlem bitene kadar kayıtlı olmayan ya da başka bir işlemde kayıtlı olamaz.  
  
> [!CAUTION]
>  `EnlistTransaction` bağlantı bağlantı kullanarak bir işlem zaten başlamış bir özel durum oluşturur <xref:System.Data.Common.DbConnection.BeginTransaction%2A> yöntemi. Ancak işlem veri kaynağında başlatılan yerel bir işlem olup olmadığını (örneğin, açıkça kullanarak BEGIN TRANSACTION deyimi yürütülürken bir <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` yerel işlem geri alma ve dağıtılmış mevcut listeleme İstenen işlem. Yerel işlem geri alındı ihbar almazsınız ve kullanmaya değil yerel işlemler yönetmelidir <xref:System.Data.Common.DbConnection.BeginTransaction%2A>. SQL Server için .NET Framework veri sağlayıcısı kullanıyorsanız (`SqlClient`) SQL Server ile listeleme girişimi bir özel durum oluşturur. Diğer tüm durumlarda algılanmayan geçer.  
  
## <a name="promotable-transactions-in-sql-server"></a>SQL Server'da promotable işlemleri  
 SQL Server, yalnızca gerekli olduğunda, yerel bir basit işlem otomatik olarak dağıtılmış bir işlem için yükseltilebilir promotable işlemleri destekler. Bir promotable işlem eklenen çağırmadığı işlemlerinin ek yükü dağıtılmış işlem ek yükü gerekli olmadığı sürece. Daha fazla bilgi ve bir kod örneği için bkz: [SQL Server ile System.Transactions tümleştirmesi](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Dağıtılmış işlemler yapılandırma  
 Dağıtılmış işlemler kullanmak için ağ üzerinden MS DTC etkinleştirmeniz gerekebilir. Windows varsa Güvenlik Duvarı etkin, ağ veya MS DTC bağlantı noktasını açmak MS DTC hizmetinin izin vermeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [SQL Server ile System.Transactions Tümleştirmesi](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
