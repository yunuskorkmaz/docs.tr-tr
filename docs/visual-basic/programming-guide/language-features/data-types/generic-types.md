---
title: "Visual Basic'de Genel Türler (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 463391da61cbafe1f50a246307994cfa134dba38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Visual Basic'de Genel Türler (Visual Basic)
A *genel tür* çeşitli veri türleri için aynı işlevleri gerçekleştirmek için uyum tek bir programlama öğesidir. Genel sınıfı veya yordam tanımladığınızda, bu işlevi gerçekleştirmek isteyebileceğiniz her bir veri türü için ayrı bir sürüm tanımlamak yok.  
  
 Benzetme çıkarılabilir kafa sayısı ile tornavida ' dir. Kapatın ve o Vidayı için doğru head seçmek için ihtiyacınız Vidayı inceleyin (yarıklı, çapraz, starred). Doğru head tornavida işleyiciyi ekledikten sonra tam aynı işlevi ile Tornavida, yani Vidayı kapatma gerçekleştirir.  
  
 ![Genel bir araç olarak tornavida diyagramı](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")  
Tornavida genel bir araç olarak ayarlayın  
  
 Genel bir tür tanımladığınızda, bir veya daha fazla veri türleriyle Parametreleştirme. Kullanarak böylece veri türleri için kendi gereksinimlerine uyarlamak için kod. Kodunuzu farklı veri türleri kümesinde çalışan her biri genel öğeden birkaç farklı programlama öğeleri bildirebilirsiniz. Ancak tüm bildirilen öğeler kullandıkları hangi veri türleri olsun aynı mantığını gerçekleştirirler.  
  
 Örneğin, belirli bir veri türüne gibi çalışır queue sınıfı oluşturmak isteyebilirsiniz `String`. Bu tür bir sınıftan bildirebilir <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 Artık kullanabilirsiniz `stringQ` özel olarak çalışmak için `String` değerleri. Çünkü `stringQ` için özel `String` için genelleştirilmiş yerine `Object` değerleri, geç bağlama veya tür dönüştürme yok. Bu, yürütme zamanı kaydeder ve çalışma zamanı hataları azaltır.  
  
 Genel bir tür kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: genel bir sınıf kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Genel bir sınıf örneği  
 Aşağıdaki örnek, genel bir sınıf iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 Önceki iskeletinde `t` olan bir *tür parametresi*, diğer bir deyişle, bir yer tutucu sınıfı bildirirken sağladığınız bir veri türü için. Başka bir yerde, kodunuzda çeşitli sürümleri bildirebilirsiniz `classHolder` çeşitli veri türleri için sağlayarak `t`. Aşağıdaki örnekte, iki tür bildirimleri gösterir.  
  
 [!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 Yukarıdaki ifadelerden bildirin *oluşturulan sınıflar*, belirli bir tür tür parametresi değiştirir. Bu değişiklik, oluşturulan sınıfın içindeki kod boyunca yayılır. Aşağıdaki örnek ne gösterir `processNewItem` gibi yordamı görünüyor `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: farklı veri türlerinde bir sınıf olduğunu olabilir sağlamak aynı işlevselliği tanımlamak](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Uygun programlama öğeleri  
 Genel sınıflar, yapılar, arabirimler, yordamlar ve temsilciler kullanın ve tanımlayın. Unutmayın [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] birkaç genel sınıflar, yapılar ve yaygın olarak kullanılan genel öğeleri temsil eden arabirimler tanımlar. <xref:System.Collections.Generic?displayProperty=nameWithType> Ad alanı, sözlük, listeler, kuyruklar ve yığınları sağlar. Genel Öğenizde tanımlamadan önce onu zaten kullanılabilir olup olmadığını <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Yordamlar türleri değildir, ancak tanımlama ve genel yordamları kullanın. Bkz: [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Genel türler avantajları  
 Genel bir tür, her biri belirli bir veri türüne üzerinde çalışır birkaç farklı programlama öğeleri bildirmek için temel olarak görev yapar. Genel bir tür alternatifleri şunlardır:  
  
1.  Üzerinde çalışan tek bir türü `Object` veri türü.  
  
2.  Bir dizi *türüne özgü* türü, her sürüm tek tek kodlanmış ve belirli bir veri türüne gibi işletim sürümlerinde `String`, `Integer`, veya kullanıcı tanımlı bir tür gibi `customer`.  
  
 Genel bir tür, bu alternatifleri aşağıdaki avantajları vardır:  
  
-   **Tür güvenliği.** Genel türler, derleme zamanı tür denetimi uygular. Türler temel alarak `Object` herhangi bir veri türü kabul edin ve bir giriş veri türü kabul edilebilir olup olmadığını denetlemek için kod yazmanız gerekir. Genel türler ile derleyici önce çalışma zamanı Tür uyuşmazlıkları yakalayabilir.  
  
-   **Performans.** Genel türler zorunda değilsiniz *kutusunu* ve *unbox* verileri, her biri bir veri türü için özelleştirilmiş olduğundan. İşlemleri temel alarak `Object` onlara dönüştürmek için giriş veri türleri kutusunda gerekir `Object` ve veri çıkışı için hedefleyen unbox. Kutulama ve kutudan çıkarma performansı düşürebilir.  
  
     Türler temel alarak `Object` üyeleri erişme ek kod çalışma zamanında gerektirdiği anlamına gelir. Ayrıca geç bağlama, şunlardır. Bu da performansı azaltır.  
  
-   **Kod birleştirme.** Genel bir tür kodda yalnızca bir kez tanımlanması gerekir. Bir türü, türe özgü sürümlerinin kümesi bu sürüm için belirli veri türü olan tek fark ile her sürümü aynı kodda çoğaltılması gerekir. Genel türler ile türüne özgü sürümleri özgün genel türden tüm üretilir.  
  
-   **Kodu yeniden kullanma.** Genel ise, belirli veri türüne bağlı değildir kod çeşitli veri türleriyle yeniden kullanılabilir. Genellikle, değil özgün tahmin bile bir veri türü ile kullanabilirsiniz.  
  
-   **IDE desteği.** Genel bir türden bildirilen oluşturulmuş bir türü kullandığınızda, kodunuzu geliştirirken tümleşik geliştirme ortamı (IDE), daha fazla destek verebilirsiniz. Örneğin, IntelliSense, bağımsız değişken türüne özgü seçeneklerini Oluşturucusu veya yönteme gösterebilirsiniz.  
  
-   **Genel algoritmaları.** Tür bağımsız soyut algoritmaları genel türleri için iyi bir aday değildir. Örneğin, sıralar genel bir yordam öğelerini kullanarak <xref:System.IComparable> arabirimini uygulayan herhangi bir veri türü ile kullanılabilir <xref:System.IComparable>.  
  
## <a name="constraints"></a>Kısıtlamalar  
 Genel tür tanımında kodu olarak türü olabildiğince bağımsız olmalıdır rağmen genel bir tür için sağlanan herhangi bir veri türü, belirli bir özelliği gerektirmesine gerekebilir. Örneğin, sıralama veya harmanlama amacıyla iki öğe karşılaştırma yapmak isterseniz, kendi veri türü uygulamalıdır <xref:System.IComparable> arabirimi. Bu gereksinim ekleyerek zorlayabilir bir *kısıtlaması* tür parametresi için.  
  
### <a name="example-of-a-constraint"></a>Bir sınırlama örneği  
 Aşağıdaki örnek, bir iskelet uygulamak için tür bağımsız değişkeni gerektiren kısıtlamasına sahip bir sınıf tanımını gösterir <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 Öğesinden bir sınıf oluşturmak sonraki kod çalışırsa `itemManager` uygulamayan bir türü sağladığını <xref:System.IComparable>, derleyici bir hata bildirir.  
  
### <a name="types-of-constraints"></a>Tür kısıtlamaları  
 Kısıtlama aşağıdaki gereksinimleri herhangi bir bileşimini belirtebilirsiniz:  
  
-   Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
-   Tür bağımsız değişkeni türünü veya gerekir en çok bir sınıftan,  
  
-   Tür bağımsız değişkeni nesneleri oluşturduğu koduna erişilebilir parametresiz bir kurucusu kullanıma sunma  
  
-   Tür bağımsız değişkeni olmalıdır bir *başvuru türüne*, veya olması gereken bir *değer türü*  
  
 Birden çok gereksinim zorunlu tuttukları gerekiyorsa, virgülle ayrılmış kullanın *sınırlama listesi* kaşlı ayraçlar içinde (`{ }`). Bir erişilebilir yapıcı gerektirecek şekilde dahil [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğü listesinde. Bir başvuru türü gerektirecek şekilde dahil `Class` bir değer türü gerektirecek şekilde anahtar sözcüğü; dahil `Structure` anahtar sözcüğü.  
  
 Kısıtlamaları hakkında daha fazla bilgi için bkz: [türü listesinde](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Birden çok kısıtlama örneği  
 Aşağıdaki örnek tür parametresi genel bir sınıf kısıtlaması listesiyle iskelet tanımını gösterir. Bu sınıfın bir örneğini oluşturur kodda, tür bağımsız değişkeni her ikisi de uygulamalıdır <xref:System.IComparable> ve <xref:System.IDisposable> arabirimleri, başvuru türünde olması gerekir ve erişilebilir bir parametresiz oluşturucuya kullanıma sunar.  
  
 [!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## <a name="important-terms"></a>Önemli terimler  
 Genel türler getirir ve aşağıdaki koşulları'nı kullanın:  
  
-   *Genel tür*. Sınıfı, yapısı, arabirim, yordam veya bunu bildirmek için en az bir veri türü sağlamak temsilci tanımıdır.  
  
-   *Type parametresi*. Türü bildirirken bir genel tür tanımı, bir veri türü için bir yer tutucu sağlayın.  
  
-   *Tür bağımsız değişkeni*. Genel bir tür oluşturulan türünden bildirirken bir tür parametresi değiştirir belirli veri türü.  
  
-   *Kısıtlama*. Tür bağımsız değişkeni kısıtlayan bir tür parametresi bir koşul için sağlayabilir. Bir kısıtlama, tür bağımsız değişkeni gerekir belirli bir arabirim uygulamak, olması veya belirli bir sınıftan, erişilebilir bir parametresiz oluşturucuya sahip veya bir başvuru türü veya bir değer türü olduğunu gerektirebilir. Bu kısıtlamaların birleştirebilirsiniz, ancak en çok bir sınıf belirtebilir.  
  
-   *Türü oluşturulan*. Sınıfı, yapısı, arabirim, yordam veya temsilci genel bir türden tür bağımsız değişkeni tür parametreleri için sağlayarak bildirildi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tür karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Veri türleri sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [,](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [Olarak](../../../../visual-basic/language-reference/statements/as-clause.md)  
 [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Kovaryans ve kontravaryans](../../concepts/covariance-contravariance/index.md)  
 [Yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
