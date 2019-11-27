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
ms.openlocfilehash: 3dcd7756b10fab8f66f4d5c10acedd8f600eb2e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350117"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Visual Basic'de Genel Türler (Visual Basic)
*Genel tür* , çeşitli veri türleri için aynı işlevselliği gerçekleştirmeye uyum sağlayan tek bir programlama öğesidir. Genel bir sınıf veya yordam tanımladığınızda, bu işlevi gerçekleştirmek isteyebileceğiniz her bir veri türü için ayrı bir sürüm tanımlamanız gerekmez.  
  
 Benzerleme vurguladı, çıkarılabilir kafaları olan bir screwdriver kümesidir. Vidalı 'yi inceleyerek, bu vidalı için doğru kafa (slosıya, çapraz, starred) açmanız ve seçmeniz gerekir. Screwdriver işleyicisine doğru bir baş ekledikten sonra, vida ' ı etkinleştirerek, Screwdriver ile tam olarak aynı işlevi gerçekleştirirsiniz.  
  
 ![Farklı kafaları olan bir screwdriver kümesi diyagramı.](./media/generic-types/generic-screwdriver-set.gif)  
  
 Genel bir tür tanımladığınızda, bir veya daha fazla veri türüyle parametreleştirebilirsiniz. Bu, veri türlerini gereksinimlerine uyarlamak için kodun kullanılmasına izin verir. Kodunuz, her biri farklı veri türleri kümesi üzerinde davranan genel öğeden birkaç farklı programlama öğesi bildirebilir. Ancak, görüntülenen öğeler, kullandıkları veri türleri ne olduğuna bakılmaksızın özdeş mantığı gerçekleştirir.  
  
 Örneğin, `String`gibi belirli bir veri türü üzerinde çalışan bir sıra sınıfı oluşturmak ve kullanmak isteyebilirsiniz. Aşağıdaki örnekte gösterildiği gibi, bu tür bir sınıfı <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>bildirebilirsiniz.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Artık, `String` değerlerle özel olarak çalışmak için `stringQ` kullanabilirsiniz. `stringQ`, `Object` değerleri için genelleştirilmesi yerine `String` özgü olduğundan, geç bağlama veya tür dönüştürme izniniz yoktur. Bu, yürütme süresini kaydeder ve çalışma zamanı hatalarını azaltır.  
  
 Genel bir tür kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: genel bir sınıf kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Genel sınıf örneği  
 Aşağıdaki örnek, bir genel sınıfın iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 Önceki iskelet 'de, `t` bir *tür parametresidir*, diğer bir deyişle, sınıfı bildirdiğinizde sağladığınız veri türü için yer tutucudur. Kodunuzun başka bir yerinde, `t`için çeşitli veri türleri sağlayarak `classHolder` çeşitli sürümlerini bildirebilirsiniz. Aşağıdaki örnek, bu iki bildirimi gösterir.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 Önceki deyimler, belirli bir türün tür parametresinin yerini aldığı *oluşturulan sınıfları*bildirir. Bu değişiklik, oluşturulan sınıf içindeki kod boyunca yayılır. Aşağıdaki örnek, `processNewItem` yordamının `integerClass`nasıl göründüğünü gösterir.  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Daha kapsamlı bir örnek için bkz. [nasıl yapılır: farklı veri türlerinde özdeş Işlevsellik sağlayabilen bir sınıf tanımlama](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Uygun programlama öğeleri  
 Genel sınıfları, yapıları, arabirimleri, yordamları ve temsilcileri tanımlayabilir ve kullanabilirsiniz. .NET Framework, yaygın olarak kullanılan genel öğeleri temsil eden çeşitli genel sınıfları, yapıları ve arabirimleri tanımladığını unutmayın. <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı sözlükler, listeleri, kuyrukları ve yığınları sağlar. Kendi genel öğesini tanımlamadan önce, <xref:System.Collections.Generic?displayProperty=nameWithType>' de zaten kullanılabilir olup olmadığını görün.  
  
 Yordamlar türler değildir, ancak genel yordamları tanımlayabilir ve kullanabilirsiniz. Bkz. [Visual Basic genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Genel türlerin avantajları  
 Genel bir tür, her biri belirli bir veri türü üzerinde çalışan birkaç farklı programlama öğesi bildirmek için temel görevi görür. Genel tür alternatifleri şunlardır:  
  
1. `Object` veri türünde çalışan tek bir tür.  
  
2. Türün *türüne özgü* bir dizi, her sürüm tek tek kodlanmış ve `String`, `Integer`veya `customer`gibi Kullanıcı tanımlı bir tür.  
  
 Genel bir tür, bu alternatifler üzerinde aşağıdaki avantajlara sahiptir:  
  
- **Tür güvenliği.** Genel türler derleme zamanı tür denetimini uygular. `Object` temel alan türler, herhangi bir veri türünü kabul eder ve bir giriş veri türünün kabul edilebilir olup olmadığını denetlemek için kod yazmanız gerekir. Genel türlerle, derleyici çalışma zamanından önce tür uyuşmazlıkları yakalayabilir.  
  
- **Mının.** Her biri bir veri türü için *özelleştirilmediği* için genel türler, verileri *Box* ve serbest bırakmak zorunda değildir. `Object` tabanlı işlemler, çıkış için hedeflenen verileri `Object` ve kutudan çıkarmak için giriş veri türleri Box olmalıdır. Kutulama ve kutudan çıkarma performansı azaltır.  
  
     `Object` tabanlı türler de geç bağlı olduğundan, üyelerine erişim çalışma zamanında ek kod gerektirir. Bu ayrıca performansı azaltır.  
  
- **Kod birleştirme.** Genel bir türdeki kodun yalnızca bir kez tanımlanması yeterlidir. Bir türün tür özgü sürümlerinin bir kümesine, her sürümde aynı kod çoğaltılmalıdır ve bu sürüm için tek fark aynı şekilde geçerlidir. Genel türler ile, türe özgü sürümlerin hepsi özgün genel türden oluşturulmuştur.  
  
- **Kod yeniden kullanımı.** Belirli bir veri türüne bağımlı olmayan kod, genel ise çeşitli veri türleriyle yeniden kullanılabilir. Genellikle, ilk olarak tahmin etmemiş olduğunuz bir veri türüyle bile onu yeniden kullanabilirsiniz.  
  
- **IDE desteği.** Genel bir türden belirtilen oluşturulmuş bir tür kullandığınızda tümleşik geliştirme ortamı (IDE), kodunuzu geliştirirken daha fazla destek verebilir. Örneğin, IntelliSense, bir oluşturucuya veya yöntemine bir bağımsız değişken için tür özgü seçenekler gösterebilir.  
  
- **Genel algoritmalar.** Tür bağımsız olan soyut algoritmalar genel türler için iyi adaylardır. Örneğin, <xref:System.IComparable> arabirimini kullanarak öğeleri sıralayan bir genel yordam, <xref:System.IComparable>uygulayan herhangi bir veri türü ile kullanılabilir.  
  
## <a name="constraints"></a>Kısıtlamalar  
 Genel tür tanımındaki kodun mümkün olduğunca bağımsız olması gerekir olsa da, genel türündefinizin verilen herhangi bir veri türünün belirli bir özelliğini sağlamanız gerekebilir. Örneğin, iki öğeyi sıralama veya harmanlama amacıyla karşılaştırmak istiyorsanız, veri türleri <xref:System.IComparable> arabirimini gerçekleştirmelidir. Tür parametresine bir *kısıtlama* ekleyerek bu gereksinimi zorunlu kılabilirsiniz.  
  
### <a name="example-of-a-constraint"></a>Kısıtlama örneği  
 Aşağıdaki örnek, <xref:System.IComparable>uygulamak için tür bağımsız değişkeni gerektiren bir kısıtlamaya sahip bir sınıfın iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Sonraki kod, <xref:System.IComparable>gerçekleştirmeyen bir tür sağlayan `itemManager` bir sınıf oluşturmaya çalışırsa, derleyici bir hata bildirir.  
  
### <a name="types-of-constraints"></a>Kısıtlama türleri  
 Kısıtlamalarınız herhangi bir kombinasyonda aşağıdaki gereksinimleri belirtebilir:  
  
- Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
- Tür bağımsız değişkeni, en fazla bir sınıfta bulunan veya ondan devralma türünden olmalıdır  
  
- Tür bağımsız değişkeni, içinden nesneler oluşturan koda erişilebilen parametresiz bir oluşturucuyu kullanıma sunmalıdır  
  
- Tür bağımsız değişkeni bir *başvuru türü*olmalı veya bir *değer türü* olmalıdır  
  
 Birden fazla gereksinim uygulamanız gerekiyorsa, küme ayraçları içinde virgülle ayrılmış bir *kısıtlama listesi* kullanın (`{ }`). Erişilebilir bir Oluşturucu istemek için, [Yeni işleç](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü listeye ekleyin. Bir başvuru türü gerektirmek için `Class` anahtar sözcüğünü dahil edersiniz. değer türü gerektirmek için `Structure` anahtar sözcüğünü dahil edersiniz.  
  
 Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Birden çok kısıtlama örneği  
 Aşağıdaki örnek, tür parametresinde kısıtlama listesi olan bir genel sınıfın iskelet tanımını gösterir. Bu sınıfın bir örneğini oluşturan kodda, tür bağımsız değişkeni hem <xref:System.IComparable> hem de <xref:System.IDisposable> arabirimlerini uygulamalıdır, bir başvuru türü olmalıdır ve erişilebilir parametresiz bir oluşturucuyu kullanıma sunar.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Önemli koşullar  
 Genel türler aşağıdaki terimleri sunar ve kullanır:  
  
- *Genel tür*. Bir sınıf, yapı, arabirim, yordam veya temsilci için en az bir veri türü sağladığınız temsilcinin tanımı.  
  
- *Tür parametresi*. Genel tür tanımında, türü bildirdiğinizde sağladığınız veri türü için yer tutucu.  
  
- *Tür bağımsız değişkeni*. Genel bir türden oluşturulmuş bir tür bildirdiğinizde bir tür parametresini değiştiren belirli bir veri türü.  
  
- *Kısıtlama*. Bir tür parametresindeki, için sağlayabilmeniz gereken tür bağımsız değişkenini kısıtlayan bir koşul. Bir kısıtlama, tür bağımsız değişkeninin belirli bir arabirim uygulaması, belirli bir sınıftan olması veya devralması, erişilebilir parametresiz bir oluşturucuya sahip olması veya bir başvuru türü ya da bir değer türü olması gerekebilir. Bu kısıtlamaları birleştirebilirsiniz, ancak en fazla bir sınıf belirtebilirsiniz.  
  
- *Oluşturulan tür*. Tür parametreleri için tür bağımsız değişkenleri sağlayarak genel bir türden belirtilen bir sınıf, yapı, arabirim, yordam veya temsilci.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Durumunu](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Gerektiği](../../../../visual-basic/language-reference/statements/as-clause.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Kovaryans ve Kontravaryans](../../concepts/covariance-contravariance/index.md)
- [Yineleyiciler](../../../../visual-basic/programming-guide/concepts/iterators.md)
