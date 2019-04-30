---
title: Yapılar ve Sınıflar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3635729705520518d4c950f8a79da7d1249285bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751078"
---
# <a name="structures-and-classes-visual-basic"></a>Yapılar ve Sınıflar (Visual Basic)
Visual Basic, yapılar ve sınıflar, her iki varlık aynı özelliklerin çoğunu destekler sonucuyla sözdizimi birleştirir. Ancak, ayrıca önemli farklar vardır yapılar ve sınıflar arasında.  
  
 Sınıfları, başvuru türleri olan avantajı sahiptir — bir başvurusu geçirme tüm veri yapısı değişkenle geçirerek daha verimlidir. Öte yandan, yapıları genel yığında bellek ayırma gerektirmez.  
  
 Bir yapısından devralınamaz çünkü yapıları genişletilmesi gerekmeyen nesneler için kullanılmalıdır. Oluşturmak istediğiniz nesne küçük örnek boyutu ve yapıları ve sınıfları performans özellikleri dikkate yapıları kullanın.  
  
## <a name="similarities"></a>Benzerlikler  
 Yapılar ve sınıflar, şu açılardan benzerdir:  
  
- Her ikisi de *kapsayıcı* türleri, içerdikleri diğer türleri üyeleri olarak anlamına gelir.  
  
- Her ikisi de, Oluşturucular, yöntemler, özellikler, alanlar, sabitleri, numaralandırmalar, olayları ve olay işleyicileri içerebilen üyeleri var. Ancak, bu üyeleri bildirilen ile karıştırmayın *öğeleri* bir yapının.  
  
- Her ikisi de üyeleri erişim düzeyleri individualized. Örneğin, bir üye bildirilebilir `Public` ve başka bir `Private`.  
  
- Her ikisi de arabirim uygulayabilir.  
  
- Her ikisi de Oluşturucular, parametrelerle veya parametresiz paylaşılan sahip.  
  
- Her ikisi de ortaya koyabileceğiniz bir *varsayılan özellik*, koşuluyla özellik en az bir parametre alır.  
  
- Her ikisi de bildirme ve olayları tetikleyebilir ve her ikisi de temsilciler bildirebilirsiniz.  
  
## <a name="differences"></a>Farkları  
 Yapılar ve sınıflar aşağıdaki Bununla farklılık gösterir:  
  
- Yapıları, *değer türleri*; sınıflardır *başvuru türleri*. Bir yapı türünün değişkenini yapısı verileri içeren yerine verileri bir sınıf türü olarak bir başvuru içeren yapar.  
  
- Yığın ayırma yapıları kullanın. yığın ayırma sınıflarını kullanın.  
  
- Tüm yapı öğeleri `Public` değişkenleri tarafından varsayılan; sınıf ve sabitler `Private` olsa da diğer sınıf üyeleri varsayılan olarak `Public` varsayılan olarak. Sınıf üyeleri için bu davranış Visual Basic 6.0 sistem varsayılanlarını ile uyumluluk sağlar.  
  
- Bir yapı paylaşılmayan en az bir değişken veya paylaşılmayan, noncustom olmalıdır; olay öğesi bir sınıf tamamen boş olabilir.  
  
- Yapı öğeleri olarak bildirilemez `Protected`; sınıf üyeleri olabilir.  
  
- Yalnızca yapı yordamı olaylarını işleyebileceğinizi bir [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` yordamı ve yalnızca, [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md); herhangi bir sınıf yordam ya da kullanarakolaylarıişleyebilir[ İşleme](../../../../visual-basic/language-reference/statements/handles-clause.md) anahtar sözcüğü veya `AddHandler` deyimi. Daha fazla bilgi için [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
- Yapı değişken bildirimleri başlatıcılar veya ilk boyutları diziler için belirtilemez; sınıf değişken bildirimlerini kullanabilirsiniz.  
  
- Yapıları örtük olarak devralmak <xref:System.ValueType?displayProperty=nameWithType> sınıfı ve her türden; devralınamaz sınıflar devralınan herhangi bir sınıf veya sınıflar dışında <xref:System.ValueType?displayProperty=nameWithType>.  
  
- Yapıları devralınabilir değil; sınıflardır.  
  
- Yapıları hiçbir zaman sonlandırılır, ortak dil çalışma zamanı (CLR) hiçbir zaman çağırır <xref:System.Object.Finalize%2A> herhangi bir yapının; metodunda sınıfları, çağıran atıktoplayıcı tarafından (GC) sonlandırılır <xref:System.Object.Finalize%2A> başvuru active vardır algıladığında bir sınıf Kalan.  
  
- Bir yapının bir oluşturucu gerektirmez; bir sınıf yapar.  
  
- Yapıları olabilir yalnızca parametreleri; izlerseniz paylaşılmayan oluşturucular sınıfları bunları parametrelerle veya parametresiz olabilir.  
  
 Her yapı daha genel bir parametresiz oluşturucu örtük daha vardır. Bu oluşturucu, yapının tüm veri öğeleri varsayılan değerlerine başlatır. Bu davranış tanımlanamaz.  
  
## <a name="instances-and-variables"></a>Örnekler ve değişkenleri  
 Yapılar değer türleri olduğundan, her bir yapı değişken kalıcı olarak tek tek yapısı örneğine bağlı. Ancak başvuru türleri sınıflardır ve bir nesne değişkeninin için çeşitli sınıf örneklerinin farklı zamanlarda başvuruda bulunabilir. Bu ayrım kullanımınızı yapılar ve sınıflar aşağıdaki şekillerde etkiler:  
  
- **Başlatma.** Yapısı değişkeni örtük olarak bir başlatma yapısı parametresiz oluşturucu kullanılarak öğeleri içerir. Bu nedenle, `Dim s As struct1` eşdeğerdir `Dim s As struct1 = New struct1()`.  
  
- **Değişkenleri atanıyor.** Başka bir yapı değişkenine atayın veya yapısı örneği için bir yordam bağımsız değişkeninin geçirmek, geçerli öğelerin değerlerinin tüm değişken yeni yapısına kopyalanır. Başka bir nesne değişkenine atayın veya bir nesne değişkeni geçirmek için bir yordam, yalnızca başvuru işaretçi kopyalanır.  
  
- **Hiçbir şey atanıyor.** Değer atayabilirsiniz [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) değişkeni, ancak örnek bir yapıya devam değişkeniyle ilişkilendirilecek. Yine, yöntemlerinin çağrılması ve değişken öğeleri atama tarafından başlatılır ancak veri öğelerine erişebilirsiniz.  
  
     Buna karşılık, bir nesne değişkeninin ayarlarsanız, `Nothing`, herhangi bir sınıfı örnekten ilişkisini kaldırın ve başka bir örneği atamak kadar hiç üye değişkeni erişemezsiniz.  
  
- **Birden çok örneği.** Bir nesne değişkeninin farklı sınıf örneklerinin farklı zamanlarda atanmış olabilir ve birden fazla nesne değişkenleri aynı anda aynı sınıf örneğine bakabilirsiniz. Sınıf üyelerinin değerlerini için yaptığınız değişiklikler, aynı örneğine işaret eden başka bir değişken üzerinden erişildiğinde bu üyeler etkiler.  
  
     Yapı öğeleri, ancak kendi örneği içinde yalıtılır. Değişiklikleri değerlerine değil yansıtılır herhangi diğer yapı değişkenleri, aynı diğer durumlarda bile `Structure` bildirimi.  
  
- **Eşitlik.** İki yapıları eşitlik testi ile bir öğeye göre test gerçekleştirilmesi gerekir. İki nesne değişkenini kullanarak karşılaştırılabilir <xref:System.Object.Equals%2A> yöntemi. <xref:System.Object.Equals%2A> iki değişken aynı örneğine kılınmayacağını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Yapılar ve Diğer Programlama Öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
