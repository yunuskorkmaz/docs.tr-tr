---
title: İşlem Desteği
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 519ddab069cf3c4ca1ccfa7b203769b8102db844
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196170"
---
# <a name="transaction-support"></a>İşlem Desteği
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üç farklı işlem modelleri destekler. Bu modeller gerçekleştirilen denetimlerini sırasına göre listelenir.  
  
## <a name="explicit-local-transaction"></a>Açık yerel işlem  
 Zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> varsa çağrılır <xref:System.Data.Linq.DataContext.Transaction%2A> özelliği bir (`IDbTransaction`) hareket <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrısı aynı işlem bağlamında gerçekleştirilir.  
  
 Yürütme veya geri alma işleminin başarılı yürütme sonrasında işlem için sizin sorumluluğunuzdur. İşlem için karşılık gelen bağlantı oluşturmak için kullanılan bağlantı eşleşmelidir <xref:System.Data.Linq.DataContext>. Farklı bir bağlantı olarak kullanılıyorsa, bir özel durum oluşturulur.  
  
## <a name="explicit-distributable-transaction"></a>Açık dağıtılabilir işlem  
 Çağırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API'leri (ancak bunlarla sınırlı olmamak üzere <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) etkin bir kapsam içinde <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrısı bir işlem kapsamında olduğunu ve yeni bir işlem oluşturmaz algılar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Ayrıca, bu durumda bağlantı kesiliyor önler. Sorgu gerçekleştirebileceğiniz ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A> böyle bir işlem yürütme bağlamı.  
  
## <a name="implicit-transaction"></a>Örtülü hareket  
 Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrısı kapsamında olup olmadığını görmek için denetimleri bir <xref:System.Transactions.Transaction> veya `Transaction` özelliği (`IDbTransaction`) kullanıcı tarafından başlatılan bir yerel işlem kümesi. Hiçbir işlem bulursa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel bir işlem başlatır (`IDbTransaction`) ve oluşturulan SQL komutları yürütme için kullanır. Tüm SQL komutları başarıyla tamamladıktan sonra [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel işlem yürütür ve döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Nasıl yapılır: İşlemleri kullanarak veri gönderimlerini köşeli ayraç](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
