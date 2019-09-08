---
title: İşlemler ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 837fe6c42d64f7416dbd895e56a38d1a409e567a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791310"
---
# <a name="transactions-and-concurrency"></a>İşlemler ve Eşzamanlılık
Bir işlem, paket olarak yürütülen tek bir komuttan veya bir komut grubundan oluşur. İşlemler, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar. İşlemdeki bir noktada bir hata oluşursa, tüm güncelleştirmeler ön işlem durumuna geri alınabilir.  
  
 Veri tutarlılığını güvence altına almak için bir işlemin ACID özelliklerine (kararlılık, tutarlılık, yalıtım ve dayanıklılık) uyması gerekir. Microsoft SQL Server gibi çoğu ilişkisel veritabanı sistemi, bir istemci uygulaması bir güncelleştirme, ekleme veya silme işlemi gerçekleştirdiğinde kilitleme, günlüğe kaydetme ve işlem yönetimi olanakları sağlayarak işlemleri destekler.  
  
> [!NOTE]
> Kilitler çok uzun tutuluyorsa birden çok kaynağı içeren işlemler eşzamanlılık daha düşük olabilir. Bu nedenle, işlemleri mümkün olduğunca kısa tutun.  
  
 Bir işlem aynı veritabanı veya sunucuda birden çok tablo içeriyorsa, saklı yordamlardaki açık işlemler genellikle daha iyi gerçekleştirilir. Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, ve `ROLLBACK TRANSACTION` deyimlerini kullanarak SQL Server saklı yordamda işlem oluşturabilirsiniz. Daha fazla bilgi için bkz. Books Online SQL Server.  
  
 SQL Server ve Oracle arasındaki bir işlem gibi farklı kaynak yöneticileriyle ilgili işlemler, dağıtılmış bir işlem gerektirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yerel İşlemler](local-transactions.md)  
 Bir veritabanına yönelik işlemlerin nasıl gerçekleştirileceğini gösterir.  
  
 [Dağıtılmış İşlemler](distributed-transactions.md)  
 ADO.NET içinde dağıtılmış işlemlerin nasıl gerçekleştirileceğini açıklar.  
  
 [SQL Server ile System.Transactions Tümleştirmesi](system-transactions-integration-with-sql-server.md)  
 Dağıtılmış <xref:System.Transactions> işlemlerle çalışmak için SQL Server ile tümleştirmeyi açıklar.  
  
 [İyimser Eşzamanlılık](optimistic-concurrency.md)  
 İyimser ve Kötümser eşzamanlılık ve eşzamanlılık ihlalleri için nasıl test kullanabileceğinizi açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlem Temelleri](../transactions/transaction-fundamentals.md)
- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [DbProviderFactories](dbproviderfactories.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
