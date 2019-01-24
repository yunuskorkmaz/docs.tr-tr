---
title: Geliştiricinin varsayılan davranışı geçersiz kılma sorumlulukları
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4773d4d5cf8192dfa1f8bfad6b5846c03ab1d2c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555628"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Geliştiricinin varsayılan davranışı geçersiz kılma sorumlulukları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki gereksinimleri uygulamaz ancak bu gereksinimler karşılanmadı varsa davranışı tanımlanmamış.  
  
-   Geçersiz kılma yöntemi değil çağırmalıdır <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veya <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu yöntemler, bir geçersiz kılma yöntemi çağrılırsa, özel durum oluşturur.  
  
-   Geçersiz kılma yöntemleri, Başlat, tamamlama veya işlem durdurmak için kullanılamaz. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> İşlemi, bir işlem altında gerçekleştirilir. Bir iç içe geçmiş işlemler dış bir işlem ile engelleyebilir. Yük geçersiz kılma yöntemleri, bir işlem başlayabilir, bunlar işlemi gerçekleştirildiğinden değil, yalnızca belirledikten sonra bir <xref:System.Transactions.Transaction>.  
  
-   Geçersiz kılma yöntemleri uygulanabilir iyimser eşzamanlılık eşleme izleyin beklenir. Aşırı yükleme yöntemini throw beklenen bir <xref:System.Data.Linq.ChangeConflictException> iyimser eşzamanlılık çakışma oluştuğunda. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu özel durumu yakalar, böylece doğru bir şekilde işleyebilir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sağlanan seçeneği <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Oluşturma (`Insert`) ve `Update` geçersiz kılma yöntemleri işlemi başarıyla tamamlandığında veritabanı üretilmiş sütuna karşılık gelen nesne üyeleri için değerlerin geri akışı beklenir.  
  
     Örneğin, varsa `Order.OrderID` bir kimlik sütununa eşlenir (*AutoIncrement* birincil anahtar), sonra `InsertOrder()` geçersiz kılma yöntemi, veritabanında oluşturulmuş Kimliği almak gerekir ve `Order.OrderID` üye bu kimliği Benzer şekilde, zaman damgası üyeleri güncelleştirilmiş nesnelerin tutarlı olduğundan emin olmak için zaman damgası veritabanında oluşturulmuş değerlerin güncelleştirilmesi gerekir. Veritabanı tarafından oluşturulan değerleri yayılması hatası, veritabanı ve tarafından izlenen nesneler arasındaki bir tutarsızlıktan neden olabilir <xref:System.Data.Linq.DataContext>.  
  
-   Doğru dinamik API'yi Çağır kullanıcının sorumluluğundadır. Örneğin, güncelleştirme yöntemi, yalnızca geçersiz kılma <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> çağrılabilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] algılamaz veya çağrılan dinamik yöntem geçerli işlemi eşleşip eşleşmediğini doğrulayın. Geçerli bir yöntemi çağrılırsa (örneğin, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> güncelleştirilmesi bir nesne için), sonuçlar tanımsızdır.  
  
-   Son olarak, belirtilen işlemi gerçekleştirmek için geçersiz kılma yöntemi bekleniyor. Semantiği [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yükleniyor, ertelenmiş istekli yükleme gibi işlemleri ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) belirtilen hizmet sağlamak için geçersiz kılma gerektirir. Örneğin, bir yük geçersiz kılar, yalnızca içeriği veritabanında olasılıkla tutarsız veri önünü açacak denetlemeden boş bir koleksiyon döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
