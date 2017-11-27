---
title: "Varsayılan davranışı geçersiz kılma, geliştirici sorumlulukları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4792967bb21912e475c32c0f37149b89a838b133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Varsayılan davranışı geçersiz kılma, geliştirici sorumlulukları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]aşağıdaki gereksinimleri zorlamaz ancak davranışı, bu gereksinimleri olmayan sağlanırsa tanımlanmadı.  
  
-   Geçersiz kılma yöntemi olmayan çağırmalısınız <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veya <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu yöntemler bir geçersiz kılma yöntemi çağrılırsa bir özel durum oluşturur.  
  
-   Geçersiz kılma yöntemleri başlatmak, yürütme veya bir işlem durdurmak için kullanılamaz. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> İşlemi, bir işlem altında gerçekleştirilir. İç içe geçmiş işlemler ile dış işlem etkileyebilir. Yük geçersiz kılma yöntemleri, bir işlem başlayabilir, bunlar işlemi içinde gerçekleştirildiği değil yalnızca belirledikten sonra bir <xref:System.Transactions.Transaction>.  
  
-   Geçersiz kılma yöntemleri geçerli iyimser eşzamanlılık eşleme izleyin beklenir. Geçersiz kılma yönteminin throw beklenen bir <xref:System.Data.Linq.ChangeConflictException> ne zaman bir iyimser eşzamanlılık çakışması ortaya çıkar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Böylece doğru şekilde işleyebilmesi için bu özel durumun yakalar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sağlanan seçenek <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Oluşturma (`Insert`) ve `Update` geçersiz kılma yöntemleri işlemi başarıyla tamamlandığında veritabanı üretilmiş sütuna karşılık gelen nesne üyeleri için değerlerin geri akış beklenir.  
  
     Örneğin, varsa `Order.OrderID` bir kimlik sütunu için eşlenen (*AutoIncrement* birincil anahtar), sonra `InsertOrder()` geçersiz kılma yöntemi veritabanında oluşturulan Kimliği almak gerekir ve `Order.OrderID` üye bu kimliği Benzer şekilde, zaman damgası üyeleri güncelleştirilmiş nesneleri tutarlı olduğundan emin olmak için veritabanında oluşturulan zaman damgası değerlerini güncellenmesi gerekiyor. Veritabanı tarafından üretilen değerler yaymak için hata neden olabilir ve veritabanı tarafından izlenen nesneler arasında bir tutarsızlık <xref:System.Data.Linq.DataContext>.  
  
-   Doğru dinamik API çağırma kullanıcının sorumluluğundadır. Örneğin, güncelleştirme yöntemi, yalnızca geçersiz kılma <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> çağrılabilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]algılamaz veya çağrılan dinamik yöntemi geçerli işlemi eşleşip eşleşmediğini doğrulayın. Uygulanamaz yöntemi çağrıldıysa (örneğin, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> güncelleştirilmesi için bir nesne için), sonuçları tanımlanmamış.  
  
-   Son olarak, belirtilen işlem için geçersiz kılma yöntemi bekleniyor. Semantiği [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yüklenirken, ertelenmiş istekli yükleme gibi işlemleri ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) belirtilen hizmet sağlamak için geçersiz kılmalar gerektirir. Örneğin, bir yük geçersiz kılar, içeriği veritabanında olasılıkla tutarsız verilere yol denetlemeden yalnızca boş bir koleksiyon döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
