---
title: Genel Türler
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
ms.openlocfilehash: b14c7a3f1f667e7c13ec0ae46185ed3ece92beb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394058"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Visual Basic'de Genel Türler (Visual Basic)
*Genel tür* , çeşitli veri türleri için aynı işlevselliği gerçekleştirmeye uyum sağlayan tek bir programlama öğesidir. Genel bir sınıf veya yordam tanımladığınızda, bu işlevi gerçekleştirmek isteyebileceğiniz her bir veri türü için ayrı bir sürüm tanımlamanız gerekmez.  
  
 Benzerleme vurguladı, çıkarılabilir kafaları olan bir screwdriver kümesidir. Vidalı 'yi inceleyerek, bu vidalı için doğru kafa (slosıya, çapraz, starred) açmanız ve seçmeniz gerekir. Screwdriver işleyicisine doğru bir baş ekledikten sonra, vida ' ı etkinleştirerek, Screwdriver ile tam olarak aynı işlevi gerçekleştirirsiniz.  
  
 ![Farklı kafaları olan bir screwdriver kümesi diyagramı.](./media/generic-types/generic-screwdriver-set.gif)  
  
 Genel bir tür tanımladığınızda, bir veya daha fazla veri türüyle parametreleştirebilirsiniz. Bu, veri türlerini gereksinimlerine uyarlamak için kodun kullanılmasına izin verir. Kodunuz, her biri farklı veri türleri kümesi üzerinde davranan genel öğeden birkaç farklı programlama öğesi bildirebilir. Ancak, görüntülenen öğeler, kullandıkları veri türleri ne olduğuna bakılmaksızın özdeş mantığı gerçekleştirir.  
  
 Örneğin, gibi belirli bir veri türü üzerinde çalışan bir sıra sınıfı oluşturmak ve kullanmak isteyebilirsiniz `String` . <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, bu tür bir sınıfı ' den bildirebilirsiniz.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Artık `stringQ` değerlerle özel olarak çalışmak için ' i kullanabilirsiniz `String` . `stringQ` `String` , Değerleri için genelleştirilmesi yerine için özel olduğundan `Object` , geç bağlama veya tür dönüştürme izniniz yoktur. Bu, yürütme süresini kaydeder ve çalışma zamanı hatalarını azaltır.  
  
 Genel bir tür kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: genel bir sınıf kullanma](how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Genel sınıf örneği  
 Aşağıdaki örnek, bir genel sınıfın iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 Önceki çatı içinde, `t` bir *tür parametresidir*, diğer bir deyişle, sınıfı bildirdiğinizde sağladığınız veri türü için bir yer tutucudur. Kodunuzun başka bir yerinde, `classHolder` için çeşitli veri türleri sunarak çeşitli sürümlerini bildirebilirsiniz `t` . Aşağıdaki örnek, bu iki bildirimi gösterir.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 Önceki deyimler, belirli bir türün tür parametresinin yerini aldığı *oluşturulan sınıfları*bildirir. Bu değişiklik, oluşturulan sınıf içindeki kod boyunca yayılır. Aşağıdaki örnek, `processNewItem` yordamının içinde nasıl göründüğünü gösterir `integerClass` .  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Daha kapsamlı bir örnek için bkz. [nasıl yapılır: farklı veri türlerinde özdeş Işlevsellik sağlayabilen bir sınıf tanımlama](how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Uygun programlama öğeleri  
 Genel sınıfları, yapıları, arabirimleri, yordamları ve temsilcileri tanımlayabilir ve kullanabilirsiniz. .NET Framework, yaygın olarak kullanılan genel öğeleri temsil eden çeşitli genel sınıfları, yapıları ve arabirimleri tanımladığını unutmayın. <xref:System.Collections.Generic?displayProperty=nameWithType>Ad alanı sözlükler, listeleri, kuyrukları ve yığınları sağlar. Kendi genel öğesini tanımlamadan önce, ' de zaten kullanılabilir olup olmadığını görün <xref:System.Collections.Generic?displayProperty=nameWithType> .  
  
 Yordamlar türler değildir, ancak genel yordamları tanımlayabilir ve kullanabilirsiniz. Bkz. [Visual Basic genel yordamlar](generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Genel türlerin avantajları  
 Genel bir tür, her biri belirli bir veri türü üzerinde çalışan birkaç farklı programlama öğesi bildirmek için temel görevi görür. Genel tür alternatifleri şunlardır:  
  
1. Veri türünde çalışan tek bir tür `Object` .  
  
2. Türün *türüne özgü* bir dizi, her sürüm tek tek kodlanmış ve, gibi belirli bir veri türü üzerinde, `String` veya gibi `Integer` Kullanıcı tanımlı bir tür `customer` .  
  
 Genel bir tür, bu alternatifler üzerinde aşağıdaki avantajlara sahiptir:  
  
- **Tür güvenliği.** Genel türler derleme zamanı tür denetimini uygular. `Object`Herhangi bir veri türünü kabul etmek için türler ve bir giriş veri türünün kabul edilebilir olup olmadığını denetlemek için kod yazmanız gerekir. Genel türlerle, derleyici çalışma zamanından önce tür uyuşmazlıkları yakalayabilir.  
  
- **Mının.** Her biri bir veri türü için *özelleştirilmediği* için genel türler, verileri *Box* ve serbest bırakmak zorunda değildir. `Object`Giriş veri türlerine göre `Object` , çıkış için hedeflenen verileri dönüştürmek ve bunları kaldırmak için gereken işlemler. Kutulama ve kutudan çıkarma performansı azaltır.  
  
     ' Ye dayalı türler `Object` de geç bağlı olduğundan, üyelerine erişim çalışma zamanında ek kod gerektirir. Bu ayrıca performansı azaltır.  
  
- **Kod birleştirme.** Genel bir türdeki kodun yalnızca bir kez tanımlanması yeterlidir. Bir türün tür özgü sürümlerinin bir kümesine, her sürümde aynı kod çoğaltılmalıdır ve bu sürüm için tek fark aynı şekilde geçerlidir. Genel türler ile, türe özgü sürümlerin hepsi özgün genel türden oluşturulmuştur.  
  
- **Kod yeniden kullanımı.** Belirli bir veri türüne bağımlı olmayan kod, genel ise çeşitli veri türleriyle yeniden kullanılabilir. Genellikle, ilk olarak tahmin etmemiş olduğunuz bir veri türüyle bile onu yeniden kullanabilirsiniz.  
  
- **IDE desteği.** Genel bir türden belirtilen oluşturulmuş bir tür kullandığınızda tümleşik geliştirme ortamı (IDE), kodunuzu geliştirirken daha fazla destek verebilir. Örneğin, IntelliSense, bir oluşturucuya veya yöntemine bir bağımsız değişken için tür özgü seçenekler gösterebilir.  
  
- **Genel algoritmalar.** Tür bağımsız olan soyut algoritmalar genel türler için iyi adaylardır. Örneğin, arabirimini kullanarak öğeleri sıralayan genel yordam, <xref:System.IComparable> uygulayan herhangi bir veri türü ile kullanılabilir <xref:System.IComparable> .  
  
## <a name="constraints"></a>Kısıtlamalar  
 Genel tür tanımındaki kodun mümkün olduğunca bağımsız olması gerekir olsa da, genel türündefinizin verilen herhangi bir veri türünün belirli bir özelliğini sağlamanız gerekebilir. Örneğin, iki öğeyi sıralama veya harmanlama amacıyla karşılaştırmak istiyorsanız, veri türlerinin arabirimini uygulaması gerekir <xref:System.IComparable> . Tür parametresine bir *kısıtlama* ekleyerek bu gereksinimi zorunlu kılabilirsiniz.  
  
### <a name="example-of-a-constraint"></a>Kısıtlama örneği  
 Aşağıdaki örnek, tür bağımsız değişkeninin uygulanmasını gerektiren kısıtlama içeren bir sınıfın iskelet tanımını gösterir <xref:System.IComparable> .  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Sonraki kod, uygulamayan bir tür sağlayan bir sınıf oluşturmaya çalışırsa `itemManager` <xref:System.IComparable> , derleyici bir hata bildirir.  
  
### <a name="types-of-constraints"></a>Kısıtlama türleri  
 Kısıtlamalarınız herhangi bir kombinasyonda aşağıdaki gereksinimleri belirtebilir:  
  
- Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
- Tür bağımsız değişkeni, en fazla bir sınıfta bulunan veya ondan devralma türünden olmalıdır  
  
- Tür bağımsız değişkeni, içinden nesneler oluşturan koda erişilebilen parametresiz bir oluşturucuyu kullanıma sunmalıdır  
  
- Tür bağımsız değişkeni bir *başvuru türü*olmalı veya bir *değer türü* olmalıdır  
  
 Birden fazla gereksinim belirlemeniz gerekiyorsa, küme ayracı () içinde virgülle ayrılmış bir *kısıtlama listesi* kullanırsınız `{ }` . Erişilebilir bir Oluşturucu istemek için, [Yeni işleç](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü listeye ekleyin. Bir başvuru türü gerektirmek için, `Class` anahtar sözcüğünü dahil edersiniz; bir değer türü gerektirmek için anahtar sözcüğünü dahil edersiniz `Structure` .  
  
 Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](../../../language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Birden çok kısıtlama örneği  
 Aşağıdaki örnek, tür parametresinde kısıtlama listesi olan bir genel sınıfın iskelet tanımını gösterir. Bu sınıfın bir örneğini oluşturan kodda, tür bağımsız değişkeni hem hem de <xref:System.IComparable> <xref:System.IDisposable> arabirimlerini uygulamalıdır, bir başvuru türü olmalıdır ve erişilebilir parametresiz bir Oluşturucu kullanıma sunar.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Önemli koşullar  
 Genel türler aşağıdaki terimleri sunar ve kullanır:  
  
- *Genel tür*. Bir sınıf, yapı, arabirim, yordam veya temsilci için en az bir veri türü sağladığınız temsilcinin tanımı.  
  
- *Tür parametresi*. Genel tür tanımında, türü bildirdiğinizde sağladığınız veri türü için yer tutucu.  
  
- *Tür bağımsız değişkeni*. Genel bir türden oluşturulmuş bir tür bildirdiğinizde bir tür parametresini değiştiren belirli bir veri türü.  
  
- *Kısıtlama*. Bir tür parametresindeki, için sağlayabilmeniz gereken tür bağımsız değişkenini kısıtlayan bir koşul. Bir kısıtlama, tür bağımsız değişkeninin belirli bir arabirim uygulaması, belirli bir sınıftan olması veya devralması, erişilebilir parametresiz bir oluşturucuya sahip olması veya bir başvuru türü ya da bir değer türü olması gerekebilir. Bu kısıtlamaları birleştirebilirsiniz, ancak en fazla bir sınıf belirtebilirsiniz.  
  
- *Oluşturulan tür*. Tür parametreleri için tür bağımsız değişkenleri sağlayarak genel bir türden belirtilen bir sınıf, yapı, arabirim, yordam veya temsilci.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Tür Karakterleri](type-characters.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Durumunu](../../../language-reference/statements/of-clause.md)
- [Gerektiği](../../../language-reference/statements/as-clause.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
- [Kovaryans ve değişken sapması](../../concepts/covariance-contravariance/index.md)
- [Yineleyiciler](../../concepts/iterators.md)
