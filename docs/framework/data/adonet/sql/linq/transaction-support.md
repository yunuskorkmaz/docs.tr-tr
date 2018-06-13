---
title: İşlem desteği
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: ff4d65c37e2d7f76c8c9f0de1de9717c8dca7b27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364983"
---
# <a name="transaction-support"></a>İşlem desteği
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üç farklı işlem modeli destekler. Aşağıda bu modeller gerçekleştirilen denetimleri sırasına göre listelenmiştir.  
  
## <a name="explicit-local-transaction"></a>Açık bir yerel işlem  
 Zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> gerekiyorsa denir <xref:System.Data.Linq.DataContext.Transaction%2A> özelliği ayarlanmış bir (`IDbTransaction`) işlem, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrısı aynı işlem bağlamında gerçekleştirilir.  
  
 Yürütme veya geri alma işlem başarılı yürütme işleminin ardından, sorumluluğundadır. İşlem için karşılık gelen bağlantı oluşturmak için kullanılan bağlantı eşleşmelidir <xref:System.Data.Linq.DataContext>. Farklı bir bağlantı kullandıysanız özel durum oluşur.  
  
## <a name="explicit-distributable-transaction"></a>Açık dağıtılabilir işlem  
 Çağırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API'leri (ancak bunlarla sınırlı olmamak dahil olmak üzere <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) etkin bir kapsamda <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrısı bir işlem kapsamı içinde olan ve yeni bir işlem oluşturmaz algılar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Ayrıca bu durumda bağlantı kesiliyor önler. Sorgu gerçekleştirebilir ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A> böyle bir işlem bağlamında yürütmeleri.  
  
## <a name="implicit-transaction"></a>Örtük işlem  
 Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrı kapsamında olup olmadığını görmek için denetimleri bir <xref:System.Transactions.Transaction> veya `Transaction` özelliği (`IDbTransaction`) kullanıcı başlatılmış bir yerel işlem ayarlayın. Hiçbir işlem bulursa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel bir işlem başlatır (`IDbTransaction`) ve oluşturulan SQL komutlarını çalıştırmak için kullanır. Tüm SQL komutları başarıyla tamamladıktan sonra [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel işlem kaydeder ve döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
