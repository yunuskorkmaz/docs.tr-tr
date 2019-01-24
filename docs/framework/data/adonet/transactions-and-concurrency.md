---
title: İşlemler ve eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: f5efa8f25e3cd4dedec9e5a9c99db28320a4d93e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494060"
---
# <a name="transactions-and-concurrency"></a>İşlemler ve eşzamanlılık
Tek bir komutu veya bir paket olarak çalıştırılacak komut grubuyla ilgili bir işlem oluşur. İşlemler, iş birden çok işlem tek bir birim halinde birleştirmek olanak tanır. İşlem bir noktadaki bir hata oluşması durumunda tüm güncelleştirmeleri geri ön işlem durumlarına geri alınabilir.  
  
 Bir işlem için ACID özellikleri uymalıdır — kararlılık, tutarlılık, yalıtım ve dayanıklılık — veri tutarlılık garantisi için. Microsoft SQL Server, bir istemci uygulama bir güncelleştirme gerçekleştirdiğinde, günlüğe kaydetme ve işlem yönetimi olanakları kilitleme sağlayarak destek işlemleri gibi çoğu ilişkisel veritabanı sistemleri ekleme veya silme işlemi.  
  
> [!NOTE]
>  Kilitleri uzun tutulur, birden fazla kaynak gerektiren işlemler eşzamanlılık düşürebilirsiniz. Bu nedenle, işlemleri olabildiğince kısa tutun.  
  
 Bir işlem birden çok tablodan aynı veritabanı veya sunucu içeriyorsa, ardından saklı yordamlarda açık işlemleri genellikle daha iyi gerçekleştirin. Transact-SQL kullanarak SQL Server saklı yordamları işlemleri oluşturabilirsiniz `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, ve `ROLLBACK TRANSACTION` deyimleri. Daha fazla bilgi için SQL Server Books Online'a bakın.  
  
 SQL Server ve Oracle, arasında bir işlem gibi farklı kaynak yöneticileri içeren işlemler, dağıtılmış bir işlem gerektirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yerel İşlemler](../../../../docs/framework/data/adonet/local-transactions.md)  
 Bir veritabanında işlemleri gerçekleştirmek üzere nasıl gösterir.  
  
 [Dağıtılmış İşlemler](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 Dağıtılmış işlemler ADO.NET yerine getirilmesi anlatılmaktadır.  
  
 [SQL Server ile System.Transactions Tümleştirmesi](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 Açıklar <xref:System.Transactions> dağıtılmış işlemler ile çalışmak için SQL Server ile tümleştirme.  
  
 [İyimser Eşzamanlılık](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 İyimser ve kötümser eşzamanlılık ve eşzamanlılık ihlaller için nasıl sınayıp doğrulayabileceğiniz açıklanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşlem Temelleri](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
