---
title: İşlem Desteği
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 1449f4d10d0feeec47ac17ffda91acb3e0da17ea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202207"
---
# <a name="transaction-support"></a>İşlem Desteği

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üç ayrı işlem modelini destekler. Aşağıda, bu modeller gerçekleştirilen denetim sırasına göre listelenmiştir.  
  
## <a name="explicit-local-transaction"></a>Açık Yerel Işlem  

 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Çağrıldığında, <xref:System.Data.Linq.DataContext.Transaction%2A> özelliği bir ( `IDbTransaction` ) işlemi olarak ayarlandıysa, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrı aynı işlem bağlamında yürütülür.  
  
 İşlemin başarılı bir şekilde yürütülmesinden sonra işlemi yürütme veya geri alma sorumluluğu sizin sorumluluğunuzdadır. İşleme karşılık gelen bağlantı, oluşturmak için kullanılan bağlantıyla aynı olmalıdır <xref:System.Data.Linq.DataContext> . Farklı bir bağlantı kullanılıyorsa bir özel durum oluşturulur.  
  
## <a name="explicit-distributable-transaction"></a>Açık dağıtılabilir Işlem  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Etkin bir kapsamda API 'leri (bunlarla sınırlı olmamak üzere <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ) çağırabilirsiniz <xref:System.Transactions.Transaction> . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrının bir işlemin kapsamında olduğunu ve yeni bir işlem oluşturmediğini algılar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Ayrıca, bu durumda bağlantının kapatılması önlenir. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Bu tür bir işlemin bağlamında sorgu ve yürütmeler gerçekleştirebilirsiniz.  
  
## <a name="implicit-transaction"></a>Örtük Işlem  

 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>' İ çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrının bir veya özelliğinin kapsamında olup olmadığını denetler <xref:System.Transactions.Transaction> `Transaction` ( `IDbTransaction` ), Kullanıcı tarafından başlatılan bir yerel işlem olarak ayarlanır. Hiç bir işlem bulmazsa, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel bir işlem ( `IDbTransaction` ) başlatır ve oluşturulan SQL komutlarını yürütmek için onu kullanır. Tüm SQL komutları başarıyla tamamlandığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel işlemi kaydeder ve döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma](how-to-bracket-data-submissions-by-using-transactions.md)
