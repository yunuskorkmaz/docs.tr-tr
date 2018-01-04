---
title: "İşlem desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 79cd52f137347ec24e7cc9a646d0306d95fe53d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-support"></a>İşlem desteği
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]üç farklı işlem modeli destekler. Aşağıda bu modeller gerçekleştirilen denetimleri sırasına göre listelenmiştir.  
  
## <a name="explicit-local-transaction"></a>Açık bir yerel işlem  
 Zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> gerekiyorsa denir <xref:System.Data.Linq.DataContext.Transaction%2A> özelliği ayarlanmış bir (`IDbTransaction`) işlem, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrısı aynı işlem bağlamında gerçekleştirilir.  
  
 Yürütme veya geri alma işlem başarılı yürütme işleminin ardından, sorumluluğundadır. İşlem için karşılık gelen bağlantı oluşturmak için kullanılan bağlantı eşleşmelidir <xref:System.Data.Linq.DataContext>. Farklı bir bağlantı kullandıysanız özel durum oluşur.  
  
## <a name="explicit-distributable-transaction"></a>Açık dağıtılabilir işlem  
 Çağırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API'leri (ancak bunlarla sınırlı olmamak dahil olmak üzere <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) etkin bir kapsamda <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çağrısı bir işlem kapsamı içinde olan ve yeni bir işlem oluşturmaz algılar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Ayrıca bu durumda bağlantı kesiliyor önler. Sorgu gerçekleştirebilir ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A> böyle bir işlem bağlamında yürütmeleri.  
  
## <a name="implicit-transaction"></a>Örtük işlem  
 Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrı kapsamında olup olmadığını görmek için denetimleri bir <xref:System.Transactions.Transaction> veya `Transaction` özelliği (`IDbTransaction`) kullanıcı başlatılmış bir yerel işlem ayarlayın. Hiçbir işlem bulursa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel bir işlem başlatır (`IDbTransaction`) ve oluşturulan SQL komutlarını çalıştırmak için kullanır. Tüm SQL komutları başarıyla tamamladıktan sonra [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel işlem kaydeder ve döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
