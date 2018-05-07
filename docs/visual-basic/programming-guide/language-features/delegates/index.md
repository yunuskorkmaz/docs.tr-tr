---
title: Temsilciler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: 99fe0eee194fae21615652c9426bf6027fbf4354
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="delegates-visual-basic"></a>Temsilciler (Visual Basic)
Temsilciler yöntemlere başvuran nesneleridir. Bunlar bazen olarak açıklanan *tür kullanımı uyumlu işlev işaretçileri* diğer programlama dillerinde kullanılan işlev işaretçileri benzer olduğundan. Ancak işlev işaretçileri, Visual Basic temsilciler sınıfına dayalı bir başvuru türü <xref:System.Delegate?displayProperty=nameWithType>. Temsilciler paylaşılan her iki yöntem başvuru — belirli bir sınıf örneği çağrılabilir yöntemleri — ve örnek yöntemleri.  
  
## <a name="delegates-and-events"></a>Temsilciler ve Olaylar  
 Temsilciler çağıran bir yordam ve çağrılan yordamı arasında bir aracı ihtiyaç duyacağınız durumlarda faydalıdır. Örneğin, farklı olay işleyicileri farklı koşullar altında arayabilmesi için olayları başlatır nesneyi isteyebilirsiniz. Ne yazık ki, olayları hangi olay işleyicisi önceden bilemezsiniz gerçekleştiren nesne belirli bir olay işliyor. Visual Basic sağlar, olayları ile dinamik olarak ilişkilendirme olay işleyicileri kullandığınızda, bir temsilci oluşturarak `AddHandler` deyimi. Çalışma zamanında temsilci uygun olay işleyicisi çağrılarını iletir.  
  
 Visual Basic temsilci oluşturur ve ayrıntılarını sizin için mvc'deki çoğu durumda, kendi temsilciler oluşturabilseniz de. Örneğin, bir `Event` deyimi dolaylı olarak adlı bir temsilci sınıf tanımlar `<EventName>EventHandler` sınıfı içeren bir iç içe geçmiş sınıf olarak `Event` deyimi ve olay ile aynı imzayla. `AddressOf` Deyimi dolaylı olarak belirli bir yordamı başvuran bir temsilci örneği oluşturur. Aşağıdaki iki kod satırı eşdeğerdir. İlk satırda açık bir örneğinin oluşturulmasını bkz `Eventhandler`, yöntem başvuru `Button1_Click` bağımsız değişken olarak gönderilir. İkinci satır aynı şeyi yapmak için daha kullanışlı bir yoludur.  
  
 [!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]  
  
 Toplu kullanabileceğiniz herhangi bir yere temsilciler derleyici oluşturma yolu temsilcinin türü kapsamında belirleyebilir.  
  
## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Var olan kullanmak bildiren olayları temsilci türüne  
 Bazı durumlarda, var olan bir temsilci türü, temel alınan temsilci olarak kullanmak için bir olay bildirmek isteyebilirsiniz. Aşağıdaki söz dizimini gösterir nasıl:  
  
 [!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]  
  
 Aynı işleyicisine birden çok olay yönlendirmek istediğinizde bu kullanışlıdır.  
  
## <a name="delegate-variables-and-parameters"></a>Temsilci değişkenleri ve parametreleri  
 Olay dışı görevleri, boş iş parçacığı oluşturma gibi veya çalışma zamanında farklı sürümlerini işlevleri çağırmak için gereken yordamları ile ilgili diğer temsilcileri kullanabilirsiniz.  
  
 Örneğin, otomobiller adlarıyla bir liste kutusu içeren bir sınıflandırılmış ad uygulaması olduğunu varsayalım. Reklamları normalde olduğundan olun araba başlığa göre sıralanır. Bazı araba yap önce araba yılın eklediğinizde, karşılaşabilecekleri bir sorun oluşur. Liste kutusu yerleşik sıralama işlevselliğini yalnızca karakter kodları tarafından sıralar sorunudur; Başlangıç tarihi ile ilk, reklam yapma ile başlayarak ve ardından tüm reklamlar yerleştirir.  
  
 Bu sorunu gidermek için standart alfabetik sıralama çoğu liste kutuları kullanır, ancak çalışma zamanında araba reklam için özel sıralama yordama geçebilirsiniz bir sınıf bir sıralama yordam oluşturabilirsiniz. Bunu yapmak için özel sıralama yordamı sıralama sınıfına çalışma zamanında temsilciler kullanarak geçirin.  
  
## <a name="addressof-and-lambda-expressions"></a>AddressOf ve Lambda ifadeleri  
 Her temsilci sınıfı nesne yöntemi belirtimi geçirilen bir oluşturucu tanımlar. Temsilci oluşturucu bağımsız değişken bir yöntem ya da bir lambda ifadesi başvuru olması gerekir.  
  
 Bir yöntem başvuru belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `AddressOf` [`expression`.]`methodName`  
  
 Derleme zamanı türünü `expression` bir sınıf veya bir yöntemi, imza eşleşen temsilci sınıfı imza belirtilen adını içeren bir arabirim adı olması gerekir. `methodName` Paylaştırılmış yöntem veya örnek yöntemi olabilir. `methodName` Sınıfının varsayılan yöntemi için bir temsilci oluşturmak olsa bile isteğe bağlı değildir.  
  
 Lambda ifadesi belirtmek için aşağıdaki sözdizimini kullanın:  
  
 `Function` ([`parm` Olarak `type`, `parm2` olarak `type2`,...]) `expression`  
  
 Aşağıdaki örnek, her ikisi de gösterir `AddressOf` ve lambda ifadeleri başvurusu için bir temsilci belirtmek için kullanılır.  
  
 [!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]  
  
 İşlev imzası temsilci türüyle eşleşmelidir. Lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md). Lambda ifadesi ile ilgili daha fazla örnekler ve `AddressOf` atamaları, temsilcilere görmek [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Temsilci Yöntemi Çağırma](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Bir yöntem bir temsilci ile ilişkilendirmek ve temsilci aracılığıyla bu yöntemi çağırmak nasıl oluşturulduğunu gösteren bir örnek sağlar.|  
|[Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Temsilciler bir yordam için başka bir yordam geçirmek için nasıl kullanılacağını gösterir.|  
|[Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|Kendi imzaları aynı olmadığında bile nasıl, alt öğeler ve işlevleri temsilciler veya işleyicileri atayabilirsiniz açıklar|  
|[Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)|Visual Basic'te olaylar genel bir bakış sağlar.|
