---
title: Dağıtılmış İşlemler
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: 143d39356f444bfc3c899164c43c9608a4aab335
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795206"
---
# <a name="distributed-transactions"></a>Dağıtılmış İşlemler
İşlem, diğer şeyler arasında bir birim olarak başarılı (işleme) veya başarısız (iptal) bir ilgili görevler kümesidir. *Dağıtılmış işlem* , çeşitli kaynakları etkileyen bir işlemdir. Dağıtılmış bir işlemin kaydedilmesi için tüm katılımcılar, verilerde yapılan değişikliklerin kalıcı olacağını garanti etmelidir. Sistem kilitlenme veya diğer öngörülemeyen olayları rağmen değişiklikleri kalıcı gerekir. Tek bir katılımcı bu garantiyi yapamazsa, tüm işlem başarısız olur ve işlemin kapsamındaki verilerde yapılan değişiklikler geri alınır.  
  
> [!NOTE]
> İşlem etkinken bir işlem başlatıldığında bir `DataReader` işlemi gerçekleştirmeyi veya geri almayı denerseniz bir özel durum oluşturulur.  
  
## <a name="working-with-systemtransactions"></a>System. Transactions ile çalışma  
 .NET Framework, dağıtılmış işlemler <xref:System.Transactions> ad alanındaki API aracılığıyla yönetilir. Birden <xref:System.Transactions> çok kalıcı Kaynak Yöneticisi dahil edildiğinde API, dağıtılmış işlem işlemesini Microsoft Dağıtılmış işlem Düzenleyicisi (MS DTC) gibi bir işlem izleyicisine devredebilir. Daha fazla bilgi için bkz. [Işlem temelleri](../transactions/transaction-fundamentals.md).  
  
 ADO.NET 2,0, bir `EnlistTransaction` <xref:System.Transactions.Transaction> örnekteki bağlantıyı listeleyen yöntemi kullanarak dağıtılmış bir işlemde bir dağıtım için destek sunmuştur. Önceki ADO.net sürümlerinde, Dağıtılmış işlemlerde açık kayıt, bir `EnlistDistributedTransaction` <xref:System.EnterpriseServices.ITransaction> örneğin bir bağlantıyı listeleme yöntemi kullanılarak, geriye dönük uyumluluk için desteklenen bir bağlantı yöntemi kullanılarak gerçekleştirildi. Enterprise Services işlemleri hakkında daha fazla bilgi için bkz. [Enterprise Services ve com+ işlemleri Ile birlikte çalışabilirlik](../transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 SQL Server veritabanına karşı <xref:System.Transactions> SQL Server için .NET Framework sağlayıcısıyla bir işlem kullanırken, hafif <xref:System.Transactions.Transaction> bir şekilde otomatik olarak kullanılacaktır. Daha sonra işlem, tam bir dağıtılmış işleme gereken şekilde yükseltilebilir. Daha fazla bilgi için bkz. [System. Transactions tümleştirmesi SQL Server](system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
> Bir Oracle veritabanının tek seferde katılabileceğiniz en fazla dağıtılmış işlem sayısı, varsayılan olarak 10 ' a ayarlanmıştır. Bir Oracle veritabanına bağlıyken 10 işlemden sonra bir özel durum oluşturulur. Oracle, dağıtılmış bir `DDL` işlemin içini desteklemez.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Dağıtılmış bir Işlemde otomatik olarak aşağı kaydetme  
 Otomatik kayıt, ADO.NET bağlantılarını `System.Transactions`tümleştirmenin varsayılan (ve tercih edilen) yoludur. Bir bağlantı nesnesi, bir işlemin etkin olduğunu belirlerse, bu bir işlemin etkin `System.Transaction` olduğunu belirlerse, bu `Transaction.Current` da null olmayan anlamına gelir. Bağlantı açıldığında otomatik işlem kaydı gerçekleşir. İşlem kapsamı içinde bir komut yürütülürse bile bu durum gerçekleşmeyecektir. Bir `Enlist=false` `OLE DB Services=-7` <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>için bağlantı dizesi parametresi olarak veya bir bağlantı dizesi parametresi olarak belirterek, mevcut hareketlerdeki otomatik kaydı devre dışı bırakabilirsiniz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> Oracle ve ODBC bağlantı dizesi parametreleri hakkında daha fazla bilgi için bkz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> . <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>ve.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Dağıtılmış bir Işlemde el ile kaydetme  
 Otomatik kayıt devre dışıysa veya bağlantı açıldıktan sonra başlatılan bir işlemi listelemesi gerekiyorsa, çalışmakta olduğunuz sağlayıcının `EnlistTransaction` <xref:System.Data.Common.DbConnection> nesne yöntemini kullanarak var olan bir dağıtılmış işlemde listeleme yapabilirsiniz kullanılarak. Varolan bir dağıtılmış işlemde en iyi şekilde, işlem yapıldığından veya geri alınırsa, veri kaynağındaki kod tarafından yapılan değişikliklerin de yürütülmesi veya geri alınması gerekir.  
  
 Dağıtılmış işlemlere son kaydetme, özellikle iş nesneleri havuzında uygulanabilir. Bir iş nesnesi açık bağlantıyla havuza alınmış ise, otomatik işlem kaydı yalnızca bağlantı açıldığında gerçekleşir. Havuza alınan iş nesnesi kullanılarak birden çok işlem gerçekleştirilirse, bu nesnenin açık bağlantısı yeni başlatılan işlemlerde otomatik olarak listelenmeyecektir. Bu durumda, bağlantı için otomatik işlem kaydı devre dışı bırakabilir ve kullanarak `EnlistTransaction`işlem sırasında bağlantı listeleme yapabilirsiniz.  
  
 `EnlistTransaction`mevcut işleme başvuru olan türde <xref:System.Transactions.Transaction> tek bir bağımsız değişken alır. Bağlantı `EnlistTransaction` yöntemini çağırdıktan sonra, bağlantı kullanılarak veri kaynağında yapılan tüm değişiklikler işleme dahil edilir. Null değer geçirilmesi, bağlantının geçerli dağıtılmış işlem listesinden listesini kaldırır. Çağrılmadan `EnlistTransaction`önce bağlantının açılması gerektiğini unutmayın.  
  
> [!NOTE]
> Bir bağlantı bir işleme açık olarak kaydedildikten sonra, ilk işlem tamamlanana kadar kaydı kaldırılamaz veya başka bir işlemde kayıtlı olamaz.  
  
> [!CAUTION]
> `EnlistTransaction`bağlantı, bağlantının <xref:System.Data.Common.DbConnection.BeginTransaction%2A> yöntemiyle zaten bir işlem başlamışsa bir özel durum oluşturur. Ancak, işlem veri kaynağında başlatılan yerel bir işlem ise (örneğin, açıkça bir <xref:System.Data.SqlClient.SqlCommand>kullanarak BEGIN TRANSACTION deyimin yürütülmesi), `EnlistTransaction` yerel işlemi ve varolan dağıtılmış istenen işlem. Yerel işlemin geri alındığı ve kullanılarak <xref:System.Data.Common.DbConnection.BeginTransaction%2A>başlatılmamış tüm yerel işlemleri yönetmesi gerektiğini fark edersiniz. SQL Server ile SQL Server (`SqlClient`) için .NET Framework veri sağlayıcısı kullanıyorsanız, listeleme girişimi bir özel durum oluşturur. Diğer tüm durumlar algılanacaktır.  
  
## <a name="promotable-transactions-in-sql-server"></a>SQL Server promotable Işlemleri  
 SQL Server, yerel bir hafif işlemin yalnızca gerekli olması durumunda otomatik olarak dağıtılmış bir işleme yükseltibileceği promotable işlemlerini destekler. Bir promotable işlemi, eklenen ek yük gerekmediği takdirde dağıtılmış bir işlemin ek yükünü çağırmaz. Daha fazla bilgi ve bir kod örneği için bkz. [SQL Server Ile System. Transactions tümleştirmesi](system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Dağıtılmış Işlemleri yapılandırma  
 Dağıtılmış işlemleri kullanabilmeniz için ağ üzerinden MS DTC 'yi etkinleştirmeniz gerekebilir. Windows Güvenlik Duvarı etkinse, MS DTC hizmetinin ağı kullanması veya MS DTC bağlantı noktasını açması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [SQL Server ile System.Transactions Tümleştirmesi](system-transactions-integration-with-sql-server.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
