---
title: Visual Basic'de Genel Türler (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 813ee167fdc09c7c7ea12f5f09602230e711d362
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593389"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Visual Basic'de Genel Türler (Visual Basic)
A *genel tür* uyum sağlayan çeşitli veri türleri için aynı işlevi gerçekleştirmek için tek bir programlama öğesi. Bir genel sınıf ya da yordamın tanımladığınızda, kendisi için bu işlevi gerçekleştirmek isteyebileceğiniz her veri türü için ayrı bir sürüm tanımlamak zorunda değildir.  
  
 Benzetme ile çıkarılabilir heads tornavida ' dir. Kapat ve bu Sarmal doğru yönelin seçin Sarmal inceleyin (yarıklı, çapraz, yıldızlı). Doğru baş tornavida tutamacın ekledikten sonra tam aynı işlevi tornavida ile yani Sarmal kapatma gerçekleştirir.  
  
 ![İle farklı heads tornavida diyagramı.](./media/generic-types/generic-screwdriver-set.gif)  
  
 Genel tür tanımlama, bir veya daha fazla veri türleriyle parametreleştirin. Kullanarak böylece veri türleri için kendi gereksinimlerine uygun hale getirmek için kod. Kodunuzu genel öğe, her biri farklı veri türleri kümesi üzerinde çalışan birkaç farklı programlama öğeleri bildirebilirsiniz. Ancak tüm bildirilen öğeler hangi veri türlerini kullandıkları ne olursa olsun aynı mantığı uygulayın.  
  
 Örneğin, oluşturma ve kullanma gibi belirli veri türü üzerinde çalışır bir kuyruk sınıfı isteyebilirsiniz `String`. Bu tür bir sınıftan bildirebilirsiniz <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Artık `stringQ` özel olarak çalışmak için `String` değerleri. Çünkü `stringQ` yönelik bir programdır `String` için genelleştirilmiş yerine `Object` değerleri geç bağlama veya türü dönüştürme yok. Bu, yürütme zaman tasarrufu sağlar ve çalışma zamanı hataları azaltır.  
  
 Genel bir tür kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Genel bir sınıf kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Genel bir sınıf örneği  
 Aşağıdaki örnek, genel bir sınıf bir çatı tanımı gösterilmektedir.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 Önceki çatıda `t` olduğu bir *tür parametresi*, diğer bir deyişle, sınıfı bildirdiğinizde, sağladığınız bir veri türü için yer tutucu. Başka bir yerde kodunuzda çeşitli sürümlerini bildirebilirsiniz `classHolder` çeşitli veri türleri için sağlama tarafından `t`. Aşağıdaki örnek, iki tür bildirimi gösterir.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 Yukarıdaki ifadelerden bildirin *oluşturulan sınıflar*, belirli bir türün tür parametresi değiştirir. Bu değişiklik, oluşturulan sınıftaki kod genelindeki yayılır. Aşağıdaki örnek, hangi gösterir `processNewItem` yordamı göründüğüne içinde `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: Farklı veri türlerinde aynı işlevselliği sağlayabilen bir sınıf tanımlama](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Uygun programlama öğeleri  
 Tanımlayabilir ve Genel sınıflar, yapılar, arabirimler, yordamları ve temsilciler kullanın. .NET Framework birkaç genel sınıflar, yapılar ve yaygın olarak kullanılan genel öğeleri temsil eden arabirimler tanımladığını unutmayın. <xref:System.Collections.Generic?displayProperty=nameWithType> Sözlükleri, listeler, kuyruklar ve Yığınlar ad alanı sağlar. Genel öğeniz tanımlamadan önce bunu zaten kullanılabilir olup olmadığını <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Yordamları türler değildir, ancak tanımlama ve genel yordamları kullanın. Bkz: [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Genel türlerin yararları  
 Genel tür, her biri belirli bir tür üzerinde çalıştığı birden fazla farklı programlama öğelerini bildirmek için temel olarak görev yapar. Genel tür alternatifleri şunlardır:  
  
1. Üzerinde çalışan tek bir tür `Object` veri türü.  
  
2. Bir dizi *türe özgü* türü, her sürüm ayrı ayrı kodlanmış ve belirli bir veri türüne gibi işletim sürümleri `String`, `Integer`, veya kullanıcı tanımlı bir tür gibi `customer`.  
  
 Genel tür, bu alternatifleri kıyasla aşağıdaki avantajlara sahiptir:  
  
- **Tür güvenliği.** Genel türler, derleme zamanı tür denetimi uygular. Türleri temel alan `Object` herhangi bir veri türü kabul edin ve bir giriş veri türü kabul edilebilir olup olmadığını denetlemek için kod yazmanız gerekir. Genel türler ile derleyici önce çalışma zamanı tür uyumsuzluklarına yakalayabilir.  
  
- **Performans.** Genel türler gerekmez *kutusu* ve *unbox* veri, çünkü her biri bir veri türü için özel olarak tasarlanmıştır. İşlemleri temel alarak `Object` kendisine dönüştürmek için giriş veri türleri kutusunda gerekir `Object` ve veri çıkışı için hedeflenen unbox. Kutulama ve kutudan çıkarma performansı düşürebilir.  
  
     Türleri temel alan `Object` olan de geç bağlanan, üyelerinin erişmek ek bir kod çalışma zamanında gerektirdiğini anlamına gelir. Bu da performansı azaltır.  
  
- **Kod birleştirme.** Kod bir genel tür içinde yalnızca bir kez tanımlanması gerekir. Bu sürüm için belirli veri türü olan tek fark ile bir dizi türüne özgü sürümleri bir türün her sürümünde, aynı kodu çoğaltılması gerekir. İle genel türleri, türe özgü sürümlerini özgün genel türden tüm oluşturulur.  
  
- **Yeniden kod.** Genel ise bir özel veri türü üzerinde benzemez kod çeşitli veri türleri ile yeniden kullanılabilir. Genellikle, olmayan ilk tahmin bile bir veri türü ile kullanabilirsiniz.  
  
- **IDE desteği.** Genel bir türden bildirilen oluşturulan tür kullandığınızda, kodunuzu geliştirirken tümleşik geliştirme ortamı (IDE), daha fazla destek verebilirsiniz. Örneğin, IntelliSense yapıcıya veya yönteme bağımsız değişken için türe özgü seçeneğine gösterebilirsiniz.  
  
- **Genel algoritmalar.** Tür bağımsız soyut algoritmalar genel türler için iyi adaylar değildir. Örneğin, sıralar, genel bir yordam öğelerini kullanarak <xref:System.IComparable> arabirimi uygulayan herhangi bir veri türü ile kullanılabilir <xref:System.IComparable>.  
  
## <a name="constraints"></a>Kısıtlamalar  
 Kodun bir genel tür tanımı olarak tür mümkün olduğu bağımsız olması olsa da, genel tür için sağlanan herhangi bir veri türü, belirli bir özelliği gerektirmesine gerekebilir. Örneğin, iki öğeyi sıralama veya harmanlama amacıyla karşılaştırmak istiyorsanız, kendi veri türü uygulamalıdır <xref:System.IComparable> arabirimi. Bu gereksinim ekleyerek zorunlu kılabilir bir *kısıtlaması* tür parametresi için.  
  
### <a name="example-of-a-constraint"></a>Sınırlama örneği  
 Aşağıdaki örnek, bir sınıf uygulamak için tür bağımsız değişkeni gerektiren kısıtlamasına sahip iskelet tanımını gösterir <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Öğesinden bir sınıf oluşturmak sonraki kod çalışırsa `itemManager` uygulamayan bir türü sağlamayı <xref:System.IComparable>, derleyici bir hata bildirir.  
  
### <a name="types-of-constraints"></a>Tür kısıtlamaları  
 Kısıtlama, herhangi bir bileşimini aşağıdaki gereksinimleri belirtebilirsiniz:  
  
- Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
- Tür bağımsız değişkeni gerekir türünde olmalı veya en fazla bir sınıftan devralma  
  
- Tür bağımsız değişkeni erişilebilir nesneleri oluşturduğu kod parametresiz bir oluşturucu kullanıma açmalıdır  
  
- Tür bağımsız değişkeni olmalıdır bir *başvuru türüne*, veya olması gereken bir *değer türü*  
  
 Birden çok gereksinimi dayatmak gerekiyorsa, virgülle ayrılmış bir kullandığınız *sınırlama listesi* kaşlı ayraçlar içinde (`{ }`). Erişilebilir bir oluşturucu gerektirecek şekilde dahil [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) listesinde anahtar sözcüğü. Bir başvuru türü gerektirecek şekilde dahil `Class` anahtar sözcüğü bir değer türü gerektirir; dahil `Structure` anahtar sözcüğü.  
  
 Kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Birden çok kısıtlaması örneği  
 Aşağıdaki örnek tür parametresi kısıtlaması listesini içeren bir genel sınıfın bir çatı tanımı gösterir. Bu sınıfın bir örneğini oluşturur kodda tür bağımsız değişkeni her ikisi de uygulamalıdır <xref:System.IComparable> ve <xref:System.IDisposable> arabirimleri, bir başvuru türü olması ve erişilebilir parametresiz bir oluşturucu üzerinden kullanıma sunacaksınız.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Önemli koşullar  
 Genel türler tanıtır ve aşağıdaki koşulları kullanın:  
  
- *Genel tür*. Sınıfı, yapıyı, arabirimi, yordamı veya bildirdiğinizde, kendisi için en az bir veri türü sağladığınız temsilci tanımı.  
  
- *Tür parametresi*. Türü bildirdiğinizde bir genel tür tanımında, siz bir veri türü için yer tutucu olarak sağlayın.  
  
- *Tür bağımsız değişkeni*. Oluşturulan tür genel bir türden bildirdiğinizde, bir tür parametresi yerini alan özel veri türü.  
  
- *Kısıtlama*. Bir koşula göre sınırlar tür bağımsız değişkeni bir tür parametresi için sağlayabilirsiniz. Bir kısıtlaması, tür bağımsız değişkeni gerekir belirli bir arabirim, olabilir veya belirli bir sınıftan, erişilebilir bir parametresiz oluşturucuya sahip veya bir başvuru türü veya değer türü olması gerektiğini gerektirebilir. Bu kısıtlamalar birleştirebilirsiniz, ancak en fazla bir sınıfı belirtebilirsiniz.  
  
- *Türü oluşturulan*. Sınıf, yapı, arabirim, yordamı veya temsilci genel bir türden tür bağımsız değişkenleri için tür parametrelerinden biri sağlanarak bildirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [,](../../../../visual-basic/language-reference/statements/of-clause.md)
- [olarak](../../../../visual-basic/language-reference/statements/as-clause.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Kovaryans ve Kontravaryans](../../concepts/covariance-contravariance/index.md)
- [Yineleyiciler](../../../../visual-basic/programming-guide/concepts/iterators.md)
