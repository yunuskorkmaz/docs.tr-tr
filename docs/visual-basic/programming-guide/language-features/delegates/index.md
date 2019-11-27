---
title: Temsilciler
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: 15b4cb0a038429c5fe67d3e013818a7a2170abcc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345233"
---
# <a name="delegates-visual-basic"></a>Temsilciler (Visual Basic)

Temsilciler yöntemlere başvuran nesnelerdir. Bazen, diğer programlama dillerinde kullanılan işlev işaretçilerine benzer olduklarından *tür açısından güvenli işlev işaretçileri* olarak açıklanırlar. Ancak işlev işaretçilerinden farklı olarak Visual Basic temsilciler, sınıf <xref:System.Delegate?displayProperty=nameWithType>dayalı bir başvuru türüdür. Temsilciler, her iki paylaşılan yönteme başvurabilir: bir sınıfın belirli bir örneği olmadan çağrılabilecek Yöntemler ve örnek yöntemleri.

## <a name="delegates-and-events"></a>Temsilciler ve Olaylar

Temsilciler, çağıran bir yordam ve çağrılan yordam arasında bir ara işlem yapmanız gereken durumlarda yararlıdır. Örneğin, olayları başlatan bir nesnenin farklı koşullarda farklı olay işleyicilerini çağırabilmesini isteyebilirsiniz. Ne yazık ki olayları oluşturan nesne, olay işleyicisinin belirli bir olayı işlemekte olduğu zamandan önce bilemez. Visual Basic, `AddHandler` ifadesini kullandığınızda sizin için bir temsilci oluşturarak olay işleyicilerini olaylarla dinamik olarak ilişkilendirmenize olanak tanır. Çalışma zamanında, temsilci çağrıları uygun olay işleyicisine iletir.

Kendi temsilcilerinizi oluşturabilseniz de çoğu durumda Visual Basic temsilciyi oluşturur ve sizin için ayrıntıları alır. Örneğin, `Event` bir ifade, `Event` ifadesini içeren sınıfın iç içe bir sınıfı olarak `<EventName>EventHandler` adlı bir temsilci sınıfını ve olayla aynı imzaya sahip olarak tanımlar. `AddressOf` deyimleri, belirli bir yordama başvuran bir temsilcinin örneğini örtülü olarak oluşturur. Aşağıdaki iki kod satırı eşdeğerdir. İlk satırda, bağımsız değişken olarak gönderilen `Button1_Click` yöntemine bir başvuruya sahip bir `EventHandler`örneğinin açıkça oluşturulmasını görürsünüz. İkinci satır, aynı şeyi yapmanın daha kolay bir yoludur.

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

Her yerde temsilci oluşturmak için kısayol yöntemini kullanabilirsiniz. derleyicinin, temsilcinin türünü bağlam tarafından belirleyebilmesi.

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Var olan bir temsilci türünü kullanan olayları bildirme

Bazı durumlarda, temel aldığı temsilci olarak var olan bir temsilci türünü kullanmak üzere bir olay bildirmek isteyebilirsiniz. Aşağıdaki sözdizimi şunları göstermektedir:

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

Bu, birden çok olayı aynı işleyiciye yönlendirmek istediğinizde yararlıdır.

## <a name="delegate-variables-and-parameters"></a>Değişkenleri ve parametreleri devretmek

Serbest iş parçacığı veya çalışma zamanında işlevlerin farklı sürümlerini çağırması gereken yordamlar gibi diğer olay dışı ilgili görevler için temsilcileri kullanabilirsiniz.

Örneğin, otomobillerin adlarını içeren bir liste kutusu içeren sınıflandırılmış bir ad uygulamanız olduğunu varsayalım. Reklamlar başlığa göre sıralanır, bu da normal olarak arabadır. Bir sorun ortaya çıktığında, bazı otomobillerin başından önce araba yılını içermesi durumunda meydana gelebilir. Sorun, liste kutusunun yerleşik sıralama işlevselliğinin yalnızca karakter kodlarına göre sıralama yaptığı bir sorundur; İlk önce tarihlerle başlayan tüm reklamları, sonra da Make ile başlayan reklamları koyar.

Bunu yapmak için, çoğu liste kutusunda standart alfabetik sıralamayı kullanan bir sınıfta sıralama yordamı oluşturabilirsiniz, ancak çalışma zamanında otomobil reklamları için özel sıralama yordamına geçiş yapabilir. Bunu yapmak için, özel sıralama yordamını, temsilciler kullanarak çalışma zamanında sıralama sınıfına geçitirsiniz.

## <a name="addressof-and-lambda-expressions"></a>AddressOf ve lambda Ifadeleri

Her temsilci sınıfı, bir nesne yönteminin belirtimini geçen bir oluşturucuyu tanımlar. Bir temsilci oluşturucusuna bağımsız değişken bir yönteme veya bir lambda ifadesine başvuru olmalıdır.

Bir yönteme başvuru belirtmek için aşağıdaki sözdizimini kullanın:

`AddressOf` [`expression`.]`methodName`

`expression` derleme zamanı türü, imzası temsilci sınıfının imzasıyla eşleşen belirtilen adda bir yöntemi içeren bir sınıfın veya arabirimin adı olmalıdır. `methodName`, paylaşılan bir yöntem ya da bir örnek yöntemi olabilir. Sınıfının varsayılan yöntemi için bir temsilci oluştursanız bile `methodName` isteğe bağlı değildir.

Bir lambda ifadesi belirtmek için aşağıdaki sözdizimini kullanın:

`Function` ([`parm` as `type`, `parm2` as `type2`,...]) `expression`

Aşağıdaki örnekte, bir temsilcinin başvurusunu belirtmek için kullanılan hem `AddressOf` hem de lambda ifadeleri gösterilmektedir.

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

İşlevin imzası, temsilci türü ile aynı olmalıdır. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md). Lambda ifadesinin daha fazla örneği ve temsilcilere `AddressOf` atamaları için bkz. [gevşek temsilci dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Temsilci Yöntemi Çağırma](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Bir yöntemi bir temsilciyle ilişkilendirmeyi ve sonra bu yöntemi temsilci aracılığıyla çağırmayı gösteren bir örnek sağlar.|
|[Nasıl yapılır: yordamları Visual Basic başka bir yordama geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Bir yordamı başka bir yordama geçirmek için temsilcilerin nasıl kullanılacağını gösterir.|
|[Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|İmzaları özdeş olmadığında bile temsilcilerin veya işleyicilere nasıl alt ve işlev atayabileceğinizi açıklar|
|[Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)|Visual Basic olaylar için bir genel bakış sağlar.|
