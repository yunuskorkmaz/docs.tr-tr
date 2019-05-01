---
title: Temsilciler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: b3f333f1714a66a8ff462000385af92cf343a19e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050603"
---
# <a name="delegates-visual-basic"></a>Temsilciler (Visual Basic)

Temsilciler, yöntemleri bakın nesnelerdir. Bunlar bazen olarak açıklanan *tür kullanımı uyumlu işlev işaretçileri* başka programlama dillerinde kullanılan işlev işaretçilerine benzer olduğundan. Ancak işlev işaretçilerinin farklı olarak, Visual Basic temsilciler sınıfına göre bir başvuru türü <xref:System.Delegate?displayProperty=nameWithType>. Temsilciler, paylaşılan iki yöntem de başvurabilir — bir sınıfın belirli bir örneği çağrılabilir yöntemleri — ve örnek yöntemler.

## <a name="delegates-and-events"></a>Temsilciler ve Olaylar

Temsilciler, çağıran yordama ve çağrılan yordam arasında bir aracı gereken durumlarda yararlıdır. Örneğin, farklı koşullarda farklı olay işleyicileri arayabilmesi için olayları oluşturan bir nesne isteyebilirsiniz. Ne yazık ki, olayları önceden hangi olay işleyicisi bilemezsiniz yükseltme nesne belirli bir olay işleme olduğu. Visual Basic sayesinde olaylarla ilişkilendirme dinamik olarak olay işleyicileri kullandığınızda, bir temsilci oluşturarak `AddHandler` deyimi. Çalışma zamanında, temsilci uygun olay işleyicisi çağrılarını iletir.

Kendi temsilcileri oluşturabilirsiniz, ancak çoğu durumda Visual Basic temsilci oluşturur ve ayrıntılarını sizin için üstlenir. Örneğin, bir `Event` ifadesi örtük olarak tanımlıyor adlı bir temsilci sınıfı `<EventName>EventHandler` sınıfını içeren bir iç içe geçmiş sınıf olarak `Event` deyimi ve olayla aynı imzaya sahip. `AddressOf` İfadesi örtük olarak belirli bir yordama başvuran bir temsilci örneğini oluşturur. Aşağıdaki iki kod satırlarını eşdeğerdir. İlk satırda açık bir örneğinin oluşturulmasını gördüğünüz `EventHandler`, bir yönteme başvuru ile `Button1_Click` bağımsız değişken olarak gönderilir. İkinci satır aynı şeyi yapmak için daha kullanışlı bir yoldur.

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

Toplu kullanabileceğiniz her yerden temsilcileri oluşturmanın derleyici yolu bağlam temsilcinin türü belirleyebilir.

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Temsilci türüne varolan kullanan bildirim olaylar

Bazı durumlarda, var olan bir temsilci türü, temel temsilci olarak kullanmak için bir olay bildirmek isteyebilirsiniz. Aşağıdaki söz dizimini gösterir nasıl:

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

Aynı işleyicisine birden fazla olay yönlendirmek istediğinizde bu kullanışlıdır.

## <a name="delegate-variables-and-parameters"></a>Temsilci değişkenleri ve parametreleri

Olay dışı görevler, çalışma zamanında farklı sürümlerini işlevleri çağırmak için gereken yordamları ile veya serbest iş parçacığı oluşturma gibi ilgili, temsilciler için kullanabilirsiniz.

Örneğin, otomobiller adlarıyla bir liste kutusunu içeren bir sınıflandırılmış ad uygulaması olduğunu varsayalım. Reklamları normalde olduğundan olun araba başlığa göre sıralanır. Yıl önce yap araba bazı bu arabalar dahil yüz bir sorun meydana gelir. Liste kutusu yerleşik sıralama işlevlerini yalnızca karakter kodlarını tarafından sıralar sorunudur; Başlangıç tarihi ile ilk, oluşturma ile başlatılıyor reklamlar tarafından izlenen tüm reklamlar yerleştirir.

Bu sorunu gidermek için standart alfabetik sıralama çoğu liste kutuları kullanır, ancak çalışma zamanında araba reklam için özel sıralama yordama geçebilirsiniz bir sınıftaki bir sıralama yordam oluşturabilirsiniz. Bunu yapmak için özel sıralama yordamı sıralama sınıfı çalışma zamanında temsilcileri kullanma geçirirsiniz.

## <a name="addressof-and-lambda-expressions"></a>AddressOf ve Lambda ifadeleri

Her bir temsilci sınıfı nesne yöntemi belirtimi geçirilen bir oluşturucu tanımlar. Bir temsilci Oluşturucu için bağımsız değişken bir yöntem veya lambda ifadesi bir başvuru olmalıdır.

Bir yönteme başvuru belirtmek için aşağıdaki sözdizimini kullanın:

`AddressOf` [`expression`.]`methodName`

Derleme zamanı türü `expression` bir sınıf veya bir yöntem imzası olan, temsilci sınıfı imzası eşleşen belirtilen adı içeren bir arabirim adı olmalıdır. `methodName` Paylaşılan bir yöntemine ya da bir örnek yöntemi olabilir. `methodName` Sınıfının varsayılan yöntemi temsilci oluşturmak olsa bile, isteğe bağlı değil.

Bir lambda ifadesini belirtmek için aşağıdaki sözdizimini kullanın:

`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`

Aşağıdaki örnek her ikisini de gösteren `AddressOf` ve lambda ifadeleri başvurusu için bir temsilci belirtmek için kullanılır.

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

İşlev imzası temsilci türüyle eşleşmelidir. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md). Lambda ifadesinin daha fazla örnek için ve `AddressOf` temsilciler için atamaları görmek [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Bir temsilci yöntemi çağırma](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Bir yöntem bir temsilci ile ilişkilendirin ve ardından o yöntemi temsilci aracılığıyla çağırmak nasıl oluşturulduğunu gösteren bir örnek sağlar.|
|[Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Bir yordam başka bir yordama geçirmeye temsilciler nasıl yapılacağı açıklanır.|
|[Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|Bile bunların imzalarını aynı olmadığında nasıl, içerdikleri ve işlevleri temsilci veya işleyicileri atayabilirsiniz açıklar|
|[Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)|Visual Basic'te olaylar genel bir bakış sağlar.|
