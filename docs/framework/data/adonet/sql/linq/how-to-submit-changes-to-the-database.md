---
title: 'Nasıl yapılır: Veritabanına Değişiklikleri Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 222ce575d9e977cc8b68862385b4a1b147c6394a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326391"
---
# <a name="how-to-submit-changes-to-the-database"></a>Nasıl yapılır: Veritabanına Değişiklikleri Gönderme
Nesnelerinizi yaptığınız kaç tane değişiklik bağımsız olarak yalnızca bellek içi çoğaltmalar için değişiklik yapılmaz. Veritabanındaki gerçek veriler için hiçbir değişiklik yaptınız. Açıkça çağırmak kadar değişikliklerinizi sunucusuna iletilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext>.  
  
 Bu çağrı yaptığınızda <xref:System.Data.Linq.DataContext> eşdeğer SQL komutları ile değişikliklerinizi çevirmek çalışır. Bu eylemler geçersiz kılmak için kendi özel mantığı kullanabilirsiniz, ancak gönderme sırası, bir hizmet tarafından düzenlenen <xref:System.Data.Linq.DataContext> olarak bilinen *işlemci değiştirme*. Olayların sırası aşağıdaki gibidir:  
  
1. Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bilinen nesne yeni örnekleri kendisine eklenmiş olan olup olmadığını belirlemek için inceler. Aksi halde, bu yeni örnekler izlenen nesneler kümesine eklenir.  
  
2. Bekleyen değişiklikleri olan tüm nesnelerin dizisini nesneleri aralarındaki bağımlılıkları göre sıralanır. Değişiklikleri diğer nesnelerine bağımlı nesneler bağımlılıklarını sonra sıralanamadı.  
  
3. Gerçek değişiklikleri hemen iletilmeden önce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tek tek komut dizisi kapsülleyen bir hareket başlatır.  
  
4. Nesnelere değişiklikleri çevrilmiş birer birer SQL komutları ve sunucuya gönderilen.  
  
 Bu noktada durdurmak gönderme işlemi veritabanı tarafından algılanan hataları neden ve bir özel durum oluşturulur. Veritabanında yapılan tüm değişiklikler geri hiçbir gönderimler hiç olmamış gibi alınır. <xref:System.Data.Linq.DataContext> Hala yapılan tüm değişikliklerin tam kayıt içeriyor. Bu nedenle sorun ve arama düzeltileceği deneyebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yeniden, aşağıdaki kod örneğinde olduğu gibi.  
  
## <a name="example"></a>Örnek  
 Gönderme işlemi başarıyla tamamlandığında <xref:System.Data.Linq.DataContext> değişiklik izleme bilgileri yoksayarak nesnelere değişiklikleri kabul eder.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)
- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
