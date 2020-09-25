---
title: 'Nasıl yapılır: Veritabanına Değişiklikleri Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 5952cce5469d7a7e13e8b896f91ea1279fd62d8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197046"
---
# <a name="how-to-submit-changes-to-the-database"></a>Nasıl yapılır: Veritabanına Değişiklikleri Gönderme

Nesneleriniz üzerinde kaç değişiklik yaptığınız fark olursa olsun, değişiklikler yalnızca bellek içi çoğaltmalar için yapılır. Veritabanındaki gerçek verilerde değişiklik yapulaştınız. Üzerinde açıkça çağrı yapana kadar değişiklikleriniz sunucuya aktarılmaz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> .  
  
 Bu çağrıyı yaptığınızda, <xref:System.Data.Linq.DataContext> değişikliklerinizi eşdeğer SQL komutlarına çevirmeye çalışır. Bu eylemleri geçersiz kılmak için kendi özel mantığınızı kullanabilirsiniz, ancak gönderim sırası <xref:System.Data.Linq.DataContext> *değişiklik işlemcisi*olarak bilinen bir hizmet tarafından düzenlenir. Olayların sırası aşağıdaki gibidir:  
  
1. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>' İ çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeni örneklerin eklenmiş olup olmadığını anlamak için bilinen nesneler kümesini inceler. Varsa, bu yeni örnekler izlenen nesneler kümesine eklenir.  
  
2. Bekleyen değişiklikleri olan tüm nesneler, aralarındaki bağımlılıklara göre nesneler dizisine göre sıralanır. Değişiklikleri diğer nesnelere bağımlı olan nesneler bağımlılıklarından sonra sıralı.  
  
3. Herhangi bir fiili değişiklik iletilmeden hemen önce, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bireysel komutların serisini kapsüllemek için bir işlem başlatır.  
  
4. Nesnelerdeki değişiklikler tek bir SQL komutlarına çevrilir ve sunucusuna gönderilir.  
  
 Bu noktada, veritabanı tarafından algılanan tüm hatalar gönderim işleminin durdurulmasına neden olur ve bir özel durum oluşur. Veritabanında yapılan tüm değişiklikler, hiçbir gönderenle gerçekleşmediği için geri alınır. <xref:System.Data.Linq.DataContext>Hala tüm değişikliklerin tam kaydına sahiptir. Bu nedenle, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Aşağıdaki kod örneğinde olduğu gibi sorunu düzeltmeyi ve yeniden aramayı deneyebilirsiniz.  
  
## <a name="example"></a>Örnek  

 Gönderim etrafındaki işlem başarıyla tamamlandığında, <xref:System.Data.Linq.DataContext> değişiklik izleme bilgilerini yoksayarak nesnelerdeki değişiklikleri kabul eder.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme](how-to-detect-and-resolve-conflicting-submissions.md)
- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
