---
title: Dağıtılmış İşlemler
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: b6553d50039ca0f4888f0610b187c6b419a462b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153205"
---
# <a name="distributed-transactions"></a>Dağıtılmış İşlemler

İşlem, diğer şeyler arasında bir birim olarak başarılı (işleme) veya başarısız (iptal) bir ilgili görevler kümesidir. *Dağıtılmış işlem* , çeşitli kaynakları etkileyen bir işlemdir. Dağıtılmış bir işlemin kaydedilmesi için tüm katılımcılar, verilerde yapılan değişikliklerin kalıcı olacağını garanti etmelidir. Sistem kilitlenme veya diğer öngörülemeyen olayları rağmen değişiklikleri kalıcı gerekir. Tek bir katılımcı bu garantiyi yapamazsa, tüm işlem başarısız olur ve işlemin kapsamındaki verilerde yapılan değişiklikler geri alınır.  
  
> [!NOTE]
> İşlem etkinken bir işlem başlatıldığında bir işlemi gerçekleştirmeyi veya geri almayı denerseniz bir özel durum oluşturulur `DataReader` .  
  
## <a name="working-with-systemtransactions"></a>System. Transactions ile çalışma  

 .NET Framework, dağıtılmış işlemler ad alanındaki API aracılığıyla yönetilir <xref:System.Transactions> . <xref:System.Transactions>Birden çok kalıcı Kaynak Yöneticisi dahil edildiğinde API, dağıtılmış işlem Işlemesini Microsoft Dağıtılmış işlem Düzenleyicisi (MS DTC) gibi bir işlem izleyicisine devredebilir. Daha fazla bilgi için bkz. [Işlem temelleri](../transactions/transaction-fundamentals.md).  
  
 ADO.NET 2,0 `EnlistTransaction` , bir örnekteki bağlantıyı listeleyen yöntemi kullanarak dağıtılmış bir işlemde bir dağıtım için destek sunmuştur <xref:System.Transactions.Transaction> . Önceki ADO.NET sürümlerinde, Dağıtılmış işlemlerde açık kayıt, `EnlistDistributedTransaction` bir örneğin bir bağlantıyı listeleme yöntemi kullanılarak <xref:System.EnterpriseServices.ITransaction> , geriye dönük uyumluluk için desteklenen bir bağlantı yöntemi kullanılarak gerçekleştirildi. Enterprise Services işlemleri hakkında daha fazla bilgi için bkz. [Enterprise Services ve com+ işlemleri Ile birlikte çalışabilirlik](../transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 <xref:System.Transactions>SQL Server veritabanına karşı SQL Server için .NET Framework sağlayıcısıyla bir işlem kullanırken, hafif bir şekilde <xref:System.Transactions.Transaction> otomatik olarak kullanılacaktır. Daha sonra işlem, tam bir dağıtılmış işleme gereken şekilde yükseltilebilir. Daha fazla bilgi için bkz. [System. Transactions tümleştirmesi SQL Server](system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
> Bir Oracle veritabanının tek seferde katılabileceğiniz en fazla dağıtılmış işlem sayısı, varsayılan olarak 10 ' a ayarlanmıştır. Bir Oracle veritabanına bağlıyken 10 işlemden sonra bir özel durum oluşturulur. Oracle, `DDL` Dağıtılmış bir işlemin içini desteklemez.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Dağıtılmış bir Işlemde otomatik olarak aşağı kaydetme  

 Otomatik kayıt, ADO.NET bağlantılarını tümleştirmenin varsayılan (ve tercih edilen) yoludur `System.Transactions` . Bir bağlantı nesnesi, bir işlemin etkin olduğunu belirlerse, bu bir işlemin etkin olduğunu belirlerse, `System.Transaction` Bu da `Transaction.Current` null olmayan anlamına gelir. Bağlantı açıldığında otomatik işlem kaydı gerçekleşir. İşlem kapsamı içinde bir komut yürütülürse bile bu durum gerçekleşmeyecektir. `Enlist=false`Bir için bağlantı dizesi parametresi olarak <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> veya bir `OLE DB Services=-7` bağlantı dizesi parametresi olarak belirterek, mevcut hareketlerdeki otomatik kaydı devre dışı bırakabilirsiniz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType> . Oracle ve ODBC bağlantı dizesi parametreleri hakkında daha fazla bilgi için bkz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType> . ve.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Dağıtılmış bir Işlemde el ile kaydetme  

 Otomatik kayıt devre dışıysa veya bağlantı açıldıktan sonra başlatılan bir işlemi listelemesi gerekiyorsa, `EnlistTransaction` <xref:System.Data.Common.DbConnection> üzerinde çalıştığınız sağlayıcının nesne yöntemini kullanarak var olan bir dağıtılmış işlemde listeleme yapabilirsiniz. Varolan bir dağıtılmış işlemde en iyi şekilde, işlem yapıldığından veya geri alınırsa, veri kaynağındaki kod tarafından yapılan değişikliklerin de yürütülmesi veya geri alınması gerekir.  
  
 Dağıtılmış işlemlere son kaydetme, özellikle iş nesneleri havuzında uygulanabilir. Bir iş nesnesi açık bağlantıyla havuza alınmış ise, otomatik işlem kaydı yalnızca bağlantı açıldığında gerçekleşir. Havuza alınan iş nesnesi kullanılarak birden çok işlem gerçekleştirilirse, bu nesnenin açık bağlantısı yeni başlatılan işlemlerde otomatik olarak listelenmeyecektir. Bu durumda, bağlantı için otomatik işlem kaydı devre dışı bırakabilir ve kullanarak işlem sırasında bağlantı listeleme yapabilirsiniz `EnlistTransaction` .  
  
 `EnlistTransaction` mevcut işleme başvuru olan türde tek bir bağımsız değişken alır <xref:System.Transactions.Transaction> . Bağlantı yöntemini çağırdıktan sonra `EnlistTransaction` , bağlantı kullanılarak veri kaynağında yapılan tüm değişiklikler işleme dahil edilir. Null değer geçirilmesi, bağlantının geçerli dağıtılmış işlem listesinden listesini kaldırır. Çağrılmadan önce bağlantının açılması gerektiğini unutmayın `EnlistTransaction` .  
  
> [!NOTE]
> Bir bağlantı bir işleme açık olarak kaydedildikten sonra, ilk işlem tamamlanana kadar kaydı kaldırılamaz veya başka bir işlemde kayıtlı olamaz.  
  
> [!CAUTION]
> `EnlistTransaction` bağlantı, bağlantının yöntemiyle zaten bir işlem başlamışsa bir özel durum oluşturur <xref:System.Data.Common.DbConnection.BeginTransaction%2A> . Bununla birlikte, işlem veri kaynağında başlatılan yerel bir işlem ise (örneğin, açıkça bir kullanarak BEGIN TRANSACTION deyimin yürütülmesi <xref:System.Data.SqlClient.SqlCommand> ), `EnlistTransaction` yerel işlemi geri alarak var olan dağıtılmış işlemde istenen şekilde Listeleme işlemini geri alacak. Yerel işlemin geri alındığı ve kullanılarak başlatılmamış tüm yerel işlemleri yönetmesi gerektiğini fark edersiniz <xref:System.Data.Common.DbConnection.BeginTransaction%2A> . SQL Server ile SQL Server () için .NET Framework Veri Sağlayıcısı kullanıyorsanız `SqlClient` , listeleme girişimi bir özel durum oluşturur. Diğer tüm durumlar algılanacaktır.  
  
## <a name="promotable-transactions-in-sql-server"></a>SQL Server promotable Işlemleri  

 SQL Server, yerel bir hafif işlemin yalnızca gerekli olması durumunda otomatik olarak dağıtılmış bir işleme yükseltibileceği promotable işlemlerini destekler. Bir promotable işlemi, eklenen ek yük gerekmediği takdirde dağıtılmış bir işlemin ek yükünü çağırmaz. Daha fazla bilgi ve bir kod örneği için bkz. [SQL Server Ile System. Transactions tümleştirmesi](system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Dağıtılmış Işlemleri yapılandırma  

 Dağıtılmış işlemleri kullanabilmeniz için ağ üzerinden MS DTC 'yi etkinleştirmeniz gerekebilir. Windows Güvenlik Duvarı etkinse, MS DTC hizmetinin ağı kullanması veya MS DTC bağlantı noktasını açması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [SQL Server ile System.Transactions Tümleştirmesi](system-transactions-integration-with-sql-server.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
