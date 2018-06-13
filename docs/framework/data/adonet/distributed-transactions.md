---
title: Dağıtılmış işlemler
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: 7792a719a73ca5183d57bcecc5d346153d824570
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766094"
---
# <a name="distributed-transactions"></a>Dağıtılmış işlemler
Bir işlem (kaydetme) başarılı ya da başka şeylerin bir birim olarak (iptal için) başarısız ilgili görevleri kümesidir. A *dağıtılmış işlem* birkaç kaynakları etkileyen bir işlem. Yürütme dağıtılmış işlem için veri herhangi bir değişiklik kalıcı olacağını tüm katılımcılar güvence altına almalıdır. Sistem kilitlenme veya diğer öngörülemeyen olayları rağmen değişiklikleri kalıcı gerekir. Bu garantisi yapmak tek bir katılımcı başarısız olursa, tüm işlem başarısız olur ve işlem kapsamı içinde veri değişiklikler geri alınır.  
  
> [!NOTE]
>  Yürütün veya bir işlem, geri çalışırsanız, bir özel durum bir `DataReader` işlem etkinken başlatıldı.  
  
## <a name="working-with-systemtransactions"></a>System.Transactions ile çalışma  
 .NET Framework'teki dağıtılmış işlemler API'si aracılığıyla yönetilen <xref:System.Transactions> ad alanı. <xref:System.Transactions> API işlem İzleyicisi Microsoft Dağıtılmış İşlem Düzenleyicisi (MS DTC) gibi birden çok kalıcı kaynak yöneticileri söz konusu olduğunda işleme dağıtılmış işlem temsilci. Daha fazla bilgi için bkz: [işlem Temelleri](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 ADO.NET 2.0 kullanarak bir dağıtılmış işlem kaydetme desteği sunmuştur `EnlistTransaction` bağlantıda kaydeder yöntemi bir <xref:System.Transactions.Transaction> örneği. ADO.NET önceki sürümlerde kullanarak dağıtılmış işlemlerin açık kaydı gerçekleştirilmedi `EnlistDistributedTransaction` yöntemi bir bağlantıda listeleme bağlantısının bir <xref:System.EnterpriseServices.ITransaction> örneği, hangi için geriye dönük uyumluluk desteklenir. Kurumsal Hizmetler işlemleri hakkında daha fazla bilgi için bkz: [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Kullanırken bir <xref:System.Transactions> işlem .NET Framework sağlayıcısı ile SQL Server için bir basit bir SQL Server veritabanında <xref:System.Transactions.Transaction> otomatik olarak kullanılacaktır. İşlem, tam bir dağıtılmış işlem gerektiği düzenli olarak sonra yükseltilebilir. Daha fazla bilgi için bkz: [SQL Server ile System.Transactions tümleştirme](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
>  Bir Oracle veritabanına aynı anda katılabilmesi için dağıtılmış işlemlerin sayısı 10'a varsayılan olarak ayarlanır. Bir Oracle veritabanına bağlandığında sonra 10 işlem özel durum oluşur. Oracle desteklemiyor `DDL` dağıtılmış işlem içinde.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Otomatik olarak bir dağıtılmış işlemde kaydetme  
 Otomatik kaydı varsayılan (ve tercih edilen) ADO.NET bağlantıları ile tümleştirme şekilde `System.Transactions`. Bir işlem etkin olmadığını belirten bir bağlantı nesnesi otomatik olarak varolan bir dağıtılmış işlemde listeleme hangi, `System.Transaction` koşulları, yani `Transaction.Current` null değil. Bağlantı açıldığında otomatik işlem kaydı oluşur. Bir komut bir işlem kapsamı içinde yürütülür olsa bile, sonra yapılmaz. Belirterek otomatik kaydı varolan işlemlerde devre dışı bırakabilirsiniz `Enlist=false` için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>, veya `OLE DB Services=-7` için bir bağlantı dizesi parametresi olarak bir <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Oracle ve ODBC bağlantı dizesi parametreleri hakkında daha fazla bilgi için bkz: <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> ve <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>El ile bir dağıtılmış işlemde kaydetme  
 Otomatik kaydı devre dışıysa veya bağlantı açıldıktan sonra başlatıldığından işlem listeleme gerekirse, varolan bir kullanarak dağıtılmış işlem listeleme `EnlistTransaction` yöntemi <xref:System.Data.Common.DbConnection> çalıştığınız sağlayıcı nesnesi ile. Varolan bir dağıtılmış işlemde kaydetme işlem yürütülmeli veya geri, veri kaynağında kodu tarafından yapılan değişiklikler yürütülmeli veya geri de, sağlar.  
  
 Dağıtılmış işlemlere kaydetme iş nesneleri havuzu olduğunda özellikle geçerlidir. Bir iş nesnesi ile açık bir bağlantı havuza varsa, bu bağlantı açıldığında otomatik işlem kaydı yalnızca oluşur. Birden çok işlem havuza alınmış iş nesnesini kullanarak gerçekleştirdiyseniz, bu nesne için açık bağlantı otomatik olarak yeni başlatılan işlemlerde listesine değil. Bu durumda, bağlantı için otomatik işlem kaydı devre dışı bırakın ve işlemleri kullanarak bağlantı listeleme `EnlistTransaction`.  
  
 `EnlistTransaction` tek bir bağımsız değişken türü <xref:System.Transactions.Transaction> diğer bir deyişle mevcut işlem başvuru. Bağlantının çağrıldıktan sonra `EnlistTransaction` yöntemi, veri kaynağı bağlantısı işlemde dahil kullanarak yapılan tüm değişiklikler. Bir null değer geçirme, geçerli bir dağıtılmış işlem kaydı bağlantısından unenlists. Çağırmadan önce bağlantıyı açılmalıdır Not `EnlistTransaction`.  
  
> [!NOTE]
>  Bağlantı bir işleme açıkça kayıtlı sonra ilk işlem tamamlanana kadar beklemediğiniz kayıtlı veya başka bir işlemde kayıtlı olamaz.  
  
> [!CAUTION]
>  `EnlistTransaction` bağlantı bağlantı kullanarak bir işlem zaten başlamış bir özel durum döndürürse <xref:System.Data.Common.DbConnection.BeginTransaction%2A> yöntemi. Ancak, işlem veri kaynağında başlatılan yerel bir işlem olup olmadığını (örneğin, açıkça kullanarak BEGIN TRANSACTION deyimi yürütme bir <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` yerel işlem geri alma ve dağıtılmış varolan listeleme İstenen işlem. Yerel işlem geri alındı bildirimi almaz ve kullanmaya değil yerel işlemler yönetmelisiniz <xref:System.Data.Common.DbConnection.BeginTransaction%2A>. SQL Server için .NET Framework veri sağlayıcısı kullanıyorsanız (`SqlClient`) SQL Server ile listeleme girişimi bir özel durum oluşturur. Diğer tüm durumlarda algılanmayan geçer.  
  
## <a name="promotable-transactions-in-sql-server"></a>SQL Server'ın yükseltilebilir işlemleri  
 SQL Server, yalnızca gerekli olduğunda, yerel bir basit işlem otomatik olarak bir dağıtılmış işlem yükseltilebilir yükseltilebilir işlemleri destekler. Yükseltilebilir işlem eklenen çağrılmaz işlemlerinin ek yükü dağıtılmış işlem eklenen ek yükü gerekli olmadığı sürece. Daha fazla bilgi ve bir kod örneği için bkz: [SQL Server ile System.Transactions tümleştirme](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Dağıtılmış işlemler yapılandırma  
 Dağıtılmış işlemler kullanmak için ağ üzerinden MS DTC etkinleştirmeniz gerekebilir. Windows varsa Güvenlik Duvarı etkinleştirildiyse, ağ kullanın veya MS DTC bağlantı noktasını açmak MS DTC hizmetinin izin vermeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [SQL Server ile System.Transactions Tümleştirmesi](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
