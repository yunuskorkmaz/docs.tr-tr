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
ms.openlocfilehash: e64b54b93463845dd9afd0c0efd0e39f20cab1ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="structures-and-classes-visual-basic"></a>Yapılar ve Sınıflar (Visual Basic)
Visual Basic yapılar ve sınıflar, her iki varlık aynı özelliklerin çoğunu destekler sonucunda sözdizimi birleştirir. Ancak, ayrıca önemli farklılıklar vardır yapılar ve sınıflar arasında.  
  
 Sınıfları, başvuru türleri olan avantajı sahiptir — bir başvuru geçirme tüm verilerini sahip bir yapı değişken geçirme daha verimlidir. Diğer taraftan, yapıları genel yığında bellek ayırma gerektirmez.  
  
 Bir yapısından devraldığı olamaz yapıları genişletilmesi gerekmeyen nesneleri kullanılmalıdır. Oluşturmak istediğiniz nesne küçük örnek boyutu olduğunda ve yapıları ve sınıfları performans özelliklerini dikkate yapıları kullanın.  
  
## <a name="similarities"></a>Benzerlikler  
 Yapılar ve sınıflar aşağıdaki yönden benzerdir:  
  
-   Her ikisi de *kapsayıcı* türleri, diğer türleri üye olarak içeren anlamına gelir.  
  
-   Hem Oluşturucular, yöntemler, özellikler, alanları, sabitleri, numaralandırmaları, olayları ve olay işleyicileri içerebilir üyeleri sahiptir. Ancak, bu üyelerle bildirilen karıştırmayın *öğeleri* bir yapısı.  
  
-   Her ikisi de üyeleri erişim düzeyleri individualized. Örneğin, bir üye bildirilebilir `Public` ve başka bir `Private`.  
  
-   Her ikisi de arabirimleri uygulayabilir.  
  
-   Her ikisi de Oluşturucular, parametre olmadan veya ile paylaşılan.  
  
-   Her ikisi de getirebilir bir *varsayılan özellik*, koşuluyla özelliği en az bir parametre alır.  
  
-   Her ikisi de bildirme ve olayları yükseltmek ve her ikisi de temsilciler bildirebilirsiniz.  
  
## <a name="differences"></a>Farkları  
 Yapılar ve sınıflar aşağıdaki gerçekleştirilebilir farklılık gösterir:  
  
-   Yapıları olan *değer türleri*; sınıflardır *başvuru türleri*. Yapı türünde bir değişken yapısı verileri içeren, yerine verileri bir sınıf türü olarak bir başvuru içeren.  
  
-   Yığın ayırma yapıları kullanın; yığın ayırma sınıflarını kullanın.  
  
-   Tüm yapısı öğeler `Public` varsayılan olarak; değişkenleri sınıf ve sabitler `Private` diğer sınıf üyeleri durumdayken varsayılan olarak, `Public` varsayılan olarak. Sınıf üyeleri için bu davranış Visual Basic 6.0 sistem varsayılanlarını ile uyumluluk sağlar.  
  
-   Bir yapı en az bir paylaşılmayan değişkeni ya da paylaşılmayan, noncustom olmalıdır olay öğesi; bir sınıf tamamen boş olabilir.  
  
-   Yapı öğeleri olarak bildirilemez `Protected`; sınıf üyeleri olabilir.  
  
-   Yalnızca bir yapı yordamı olayları işleyebilirsiniz bir [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` yordamı ve yalnızca, [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md); herhangi bir sınıf yordamı ya da kullanarakolaylarıişleyebilir[ İşleme](../../../../visual-basic/language-reference/statements/handles-clause.md) anahtar sözcüğü veya `AddHandler` deyimi. Daha fazla bilgi için bkz: [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Yapı değişken bildirimleri başlatıcıları ya da diziler için başlangıç boyutlar belirtemezsiniz; sınıf değişken bildirimleri olabilir.  
  
-   Yapıları örtük olarak devral <xref:System.ValueType?displayProperty=nameWithType> sınıfı ve herhangi diğer türünden; devralır olamaz sınıfları devral herhangi bir sınıf veya sınıfları dışında <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Yapıları devralınabilir değil; sınıflarıdır.  
  
-   Yapıları hiçbir zaman sonlandırıldı, ortak dil çalışma zamanı (CLR) hiçbir zaman çağırır <xref:System.Object.Finalize%2A> herhangi bir yapısını; yöntemini çağıran atıktoplayıcı tarafından (GC) sınıfları sona erdirildi <xref:System.Object.Finalize%2A> etkin başvuru vardır algıladığında bir sınıf Kalan.  
  
-   Bir yapı bir oluşturucu gerektirmez; bir sınıf yapar.  
  
-   Yapıları olabilir yalnızca parametreleri; izlerseniz paylaşılmayan oluşturucular sınıfları bunları ile veya parametresiz sahip olabilir.  
  
 Her yapısı daha genel bir parametresiz oluşturucuya örtük daha vardır. Bu oluşturucu, tüm yapısı veri öğeleri varsayılan değerlerine başlatır. Bu davranış tanımlanamaz.  
  
## <a name="instances-and-variables"></a>Örnekler ve değişkenleri  
 Yapılar değer türleri olduğundan, her bir yapı değişken kalıcı olarak tek tek yapısı örneğine bağlı. Ancak başvuru türleri sınıflardır ve bir nesne değişkeni çeşitli sınıf örnekleri farklı zamanlarda başvuruda bulunabilir. Bu ayrım yapılar ve sınıflar kullanımınızı aşağıdaki şekillerde etkiler:  
  
-   **başlatma.** Yapısı değişkeni örtük olarak bir başlatma yapısı parametresiz bir kurucusu kullanarak tüm öğeleri içerir. Bu nedenle, `Dim s As struct1` eşdeğerdir `Dim s As struct1 = New struct1()`.  
  
-   **Değişkenleri atama.** Başka bir yapı değişkeni atamak veya bir yordam bağımsız değişkeninin bir yapısı örneği geçirmek, değişken tüm öğeleri geçerli değerlerini yeni yapısına kopyalanır. Başka bir nesne değişkeni atamak veya bir nesne değişkeninin bir yordama geçmesi durumunda yalnızca başvuru işaretçisi kopyalanır.  
  
-   **Hiçbir şey atama.** Değer atayabilirsiniz [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) değişkeni ancak örnek bir yapıya devam değişkeni ile ilişkili olmalıdır. Hala yöntemlerini çağırın ve değişken öğeleri atama tarafından yeniden olsa da, kendi veri öğeleri erişebilirsiniz.  
  
     Buna karşılık, bir nesne değişkeni ayarlarsanız, `Nothing`, herhangi bir sınıfı örnekten ilişkilendirmesini kaldırmanız ve başka bir örneği atayana kadar hiç üye değişkeni erişilemiyor.  
  
-   **Birden çok örneği.** Bir nesne değişkeni farklı zamanlarda atanmış farklı sınıf örnekleri olabilir ve birden fazla nesne değişkenleri aynı anda aynı sınıf örneğine bakın. Sınıf üyeleri değerleri için yaptığınız değişiklikler aynı örneğini işaret eden başka bir değişken üzerinden erişildiğinde bu üyeler etkiler.  
  
     Yapı öğeleri, ancak kendi örneğinde yalıtılır. Değişiklikleri değerlerine değil yansıtılır herhangi diğer yapı değişkenleri, aynı diğer durumlarda bile `Structure` bildirimi.  
  
-   **Eşitlik.** İki yapılarını eşitlik sınamasını ile öğesi öğeli test gerçekleştirilmesi gerekir. İki nesne değişkenleri kullanarak karşılaştırılabilir <xref:System.Object.Equals%2A> yöntemi. <xref:System.Object.Equals%2A> iki değişken aynı örneğini olup olmadığını gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Yapılar ve Diğer Programlama Öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
