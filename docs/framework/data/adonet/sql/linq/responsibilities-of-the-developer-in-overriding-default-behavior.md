---
title: Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4bfb108e81f64ea368c6bcc846553eb1af5c23b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792732"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aşağıdaki gereksinimleri zorunlu kılmaz, ancak bu gereksinimler karşılanmıyorsa davranış tanımsızdır.  
  
- Geçersiz kılma yöntemi veya <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.Table%601.Attach%2A>çağrısını içermemelidir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu yöntemler bir geçersiz kılma yönteminde çağrılırsa bir özel durum oluşturur.  
  
- Geçersiz kılma yöntemleri bir işlemi başlatmak, yürütmek veya durdurmak için kullanılamaz. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> İşlem bir işlem altında gerçekleştirilir. İç içe geçmiş bir işlem, dış işlem ile karışabilir. Yük geçersiz kılma yöntemleri, bir işlemi yalnızca işlemin bir <xref:System.Transactions.Transaction>içinde gerçekleştirilmediğini belirledikten sonra başlatabilir.  
  
- Geçersiz kılma yöntemlerinin, geçerli iyimser eşzamanlılık eşlemesini izlemesi beklenir. Bir iyimser eşzamanlılık çakışması oluştuğunda, geçersiz kılma <xref:System.Data.Linq.ChangeConflictException> yönteminin bir oluşturması beklenir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde<xref:System.Data.Linq.DataContext.SubmitChanges%2A>belirtilen seçeneği doğru şekilde işleyebilmeniz için bu özel durumu yakalar.  
  
- Oluşturma (`Insert`) ve `Update` geçersiz kılma yöntemlerinin, işlem başarıyla tamamlandığında veritabanı tarafından oluşturulan sütunların değerlerini karşılık gelen nesne üyelerine yeniden akışı beklenir.  
  
     Örneğin, `Order.OrderID` bir kimlik sütunuyla (*AutoIncrement* birincil anahtar `InsertOrder()` ) eşlenmişse, geçersiz kılma yöntemi `Order.OrderID` veritabanı tarafından üretilen kimliği almalıdır ve üyeyi bu kimliğe göre ayarlar. Benzer şekilde, güncelleştirilmiş nesnelerin tutarlı olduğundan emin olmak için zaman damgası üyeleri veritabanı tarafından oluşturulan zaman damgası değerlerine güncelleştirilmeleri gerekir. Veritabanı tarafından oluşturulan değerlerin yayamaması, <xref:System.Data.Linq.DataContext>veritabanı ile tarafından izlenen nesneler arasında tutarsızlığa neden olabilir.  
  
- Doğru dinamik API 'YI çağırmak kullanıcının sorumluluğundadır. Örneğin, Update override yönteminde yalnızca, <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> çağrılabilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çağrılan dinamik yöntemin geçerli işlemle eşleşip eşleşmediğini algılamaz veya doğrulamaz. Uygun bir yöntem çağrılırsa (örneğin, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> bir nesnenin güncelleştirilebilmesi için), sonuçlar tanımsızdır.  
  
- Son olarak, geçersiz kılma yöntemi belirtilen işlemi gerçekleştirmek için beklenmektedir. Eager yükleme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , ertelenmiş yükleme ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) gibi işlemlerin semantiğinin, belirtilen hizmeti sağlaması için geçersiz kılmaların olması gerekir. Örneğin, veritabanının içeriğini denetlemeden yalnızca boş bir koleksiyon döndüren bir yük geçersiz kılma muhtemelen tutarsız verilere neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Insert, Update ve Delete İşlemlerini Özelleştirme](customizing-insert-update-and-delete-operations.md)
