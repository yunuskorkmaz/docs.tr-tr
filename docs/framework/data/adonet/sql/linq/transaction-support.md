---
title: İşlem desteği
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: f53a6081102991c73543b4cd76365f7e2c0faf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517207"
---
# <a name="transaction-support"></a>İşlem desteği
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
