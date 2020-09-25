---
title: Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 88a7076e12e39ed23aa6d661aa90f74258f3dded
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200439"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , aşağıdaki gereksinimleri zorunlu kılmaz, ancak bu gereksinimler karşılanmıyorsa davranış tanımsızdır.  
  
- Geçersiz kılma yöntemi veya çağrısını içermemelidir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.Table%601.Attach%2A> . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu yöntemler bir geçersiz kılma yönteminde çağrılırsa bir özel durum oluşturur.  
  
- Geçersiz kılma yöntemleri bir işlemi başlatmak, yürütmek veya durdurmak için kullanılamaz. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>İşlem bir işlem altında gerçekleştirilir. İç içe geçmiş bir işlem, dış işlem ile karışabilir. Yük geçersiz kılma yöntemleri, bir işlemi yalnızca işlemin bir içinde gerçekleştirilmediğini belirledikten sonra başlatabilir <xref:System.Transactions.Transaction> .  
  
- Geçersiz kılma yöntemlerinin, geçerli iyimser eşzamanlılık eşlemesini izlemesi beklenir. Bir iyimser eşzamanlılık çakışması oluştuğunda, geçersiz kılma yönteminin bir oluşturması beklenir <xref:System.Data.Linq.ChangeConflictException> . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üzerinde belirtilen seçeneği doğru şekilde işleyebilmeniz için bu özel durumu yakalar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .  
  
- Oluşturma ( `Insert` ) ve `Update` geçersiz kılma yöntemlerinin, işlem başarıyla tamamlandığında veritabanı tarafından oluşturulan sütunların değerlerini karşılık gelen nesne üyelerine yeniden akışı beklenir.  
  
     Örneğin, `Order.OrderID` bir kimlik sütunuyla (*AutoIncrement* birincil anahtar) eşlenmişse, `InsertOrder()` geçersiz kılma YÖNTEMI veritabanı tarafından üretilen kimliği ALMALıDıR ve `Order.OrderID` üyeyi bu kimliğe göre ayarlar. Benzer şekilde, güncelleştirilmiş nesnelerin tutarlı olduğundan emin olmak için zaman damgası üyeleri veritabanı tarafından oluşturulan zaman damgası değerlerine güncelleştirilmeleri gerekir. Veritabanı tarafından oluşturulan değerlerin yayamaması, veritabanı ile tarafından izlenen nesneler arasında tutarsızlığa neden olabilir <xref:System.Data.Linq.DataContext> .  
  
- Doğru dinamik API 'YI çağırmak kullanıcının sorumluluğundadır. Örneğin, Update override yönteminde yalnızca, <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> çağrılabilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrılan dinamik yöntemin geçerli işlemle eşleşip eşleşmediğini algılamaz veya doğrulamaz. Uygun bir yöntem çağrılırsa (örneğin, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> bir nesnenin güncelleştirilebilmesi için), sonuçlar tanımsızdır.  
  
- Son olarak, geçersiz kılma yöntemi belirtilen işlemi gerçekleştirmek için beklenmektedir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Eager yükleme, ertelenmiş yükleme ve) gibi işlemlerin semantiğinin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> belirtilen hizmeti sağlaması için geçersiz kılmaların olması gerekir. Örneğin, veritabanının içeriğini denetlemeden yalnızca boş bir koleksiyon döndüren bir yük geçersiz kılma muhtemelen tutarsız verilere neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Insert, Update ve Delete İşlemlerini Özelleştirme](customizing-insert-update-and-delete-operations.md)
