---
title: Bir Visual Basic Programının Yapısı
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 5c45cc8982a03d5bdd974434164187b03529ae05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="structure-of-a-visual-basic-program"></a>Bir Visual Basic Programının Yapısı
Visual Basic programı standart yapı taşları oluşturulmuştur. A *çözüm* bir veya daha fazla projeleri içerir. A *proje* bir veya daha fazla derlemeleri sırayla içerebilir. Her *derleme* bir veya daha fazla kaynak dosyalarından derlenir. A *kaynak dosyası* tanımı ve uygulama sınıflar, yapılar, modüller ve sonuç olarak tüm kodunuzu içeren arabirimleri sağlar.  
  
 Visual Basic programı bu yapı taşları hakkında daha fazla bilgi için bkz: [çözümler ve projeler](/visualstudio/ide/solutions-and-projects-in-visual-studio) ve [derlemeler ve genel derleme önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
## <a name="file-level-programming-elements"></a>Dosya düzeyinde programlama öğeleri  
 Bir proje veya dosya başlatın ve Kod Düzenleyicisi'ni açın, biraz kod zaten yerinde ve doğru sırada bakın. Yazdığınız herhangi bir kod aşağıdaki sırayı izlemelisiniz:  
  
1.  `Option` Deyimleri  
  
2.  `Imports` Deyimleri  
  
3.  `Namespace` ifadeler ve ad alanı düzeyinde öğeleri  
  
 Farklı bir sırada deyimleri girerseniz, derleme hataları neden olabilir.  
  
 Bir program koşullu derleme deyimleri de içerebilir. Bunlar önceki dizisi deyimleri arasında kaynak dosyasında intersperse.  
  
### <a name="option-statements"></a>Seçenek deyimleri  
 `Option` deyimleri izleyen kod, sözdizimi ve mantık hataları önlemeye yardımcı olmak için başından başlayarak kurallar oluşturun. [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md) tüm değişkenleri bildirilir ve doğru yazıldığından emin, hata ayıklama süresini azaltır sağlar. [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) farklı veri türleri değişkenleri arasında çalışırken oluşabilecek mantık hataları ve veri kaybını en aza indirmek için yardımcı olur. [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md) şekilde dizeleri birbirlerine, üzerinde bağlı karşılaştırılır belirtir kendi `Binary` veya `Text` değerleri.  
  
### <a name="imports-statements"></a>İçeri aktarmalar deyimleri  
 Dahil edebileceğiniz bir [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dışında proje tanımlanan adları almak için. Bir `Imports` deyimi sınıfları ve bunları uygun gerek kalmadan içeri aktarılan ad alanı içinde tanımlanan diğer türleri başvurmak kodunuzu sağlar. Birçok kullanabileceğiniz `Imports` deyimleri uygun şekilde. Daha fazla bilgi için bkz: [References ve Imports deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Namespace deyimleri  
 Düzenlemek ve programlama öğelerinizi gruplandırma ve erişim kolaylığı için Sınıflandır ad alanları yardımcı olur. Kullandığınız [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md) aşağıdaki deyimleri belirli bir ad alanı içinde sınıflandırmak için. Daha fazla bilgi için bkz: [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Koşullu derleme deyimleri  
 Koşullu derleme deyimleri neredeyse her yerden kaynak dosyanızda yer alabilir. Bunlar, dahil edilecek veya belirli koşullara bağlı olarak derleme zamanında hariç için kodunuzu bölümlerini neden. Koşullu kod modu yalnızca hata ayıklama çalıştığından, ayrıca bunları uygulamanızın, hata ayıklama için kullanabilirsiniz. Daha fazla bilgi için bkz: [koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Namespace düzeyi programlama öğeleri  
 Sınıflar, yapılar ve modülleri kaynak dosyanızdaki tüm kod içerir. Bunlar *ad alanı düzeyinde* bir ad alanı içinde veya kaynak dosya düzeyinde görünebilir öğeleri. Bunlar, diğer programlama öğeleri bildirimlerini basılı tutun. Öğe imzaları tanımlamak, ancak hiçbir uygulama sunmak, arabirimleri, aynı zamanda Modül düzeyinde görüntülenir. Modül düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:  
  
-   [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Veri ad alanı düzeyinde sabit listeleri ve temsilciler öğelerdir.  
  
## <a name="module-level-programming-elements"></a>Modül düzeyi programlama öğeleri  
 Yordamlar, işleçleri, özellikleri ve olayları yürütülebilir kod (çalışma zamanında eylemleri gerçekleştirme deyimleri) tutabileceği yalnızca programlama öğelerdir. Bunlar *modül düzeyi* programınızın öğeleri. Yordam düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:  
  
-   [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Veri modülü düzeyinde değişkenlerinin, sabitleri, numaralandırmaları ve temsilciler öğelerdir.  
  
## <a name="procedure-level-programming-elements"></a>Yordam düzeyi programlama öğeleri  
 Çoğu içeriğinin *yordam düzeyi* , programın çalışma zamanı kodu oluşturan executable deyimleri öğeleridir. Tüm yürütülebilir kod bazı yordamda olmalıdır (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Daha fazla bilgi için bkz: [deyimleri](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Veri öğeleri yordamı düzeyinde, yerel değişkenleri ve sabitleri sınırlıdır.  
  
## <a name="the-main-procedure"></a>Main yordamı  
 `Main` Uygulamanızı yüklendiğinde çalıştırmak için ilk kod bir yordamdır. `Main` Uygulamanız için genel denetim ve başlangıç noktası olarak görevi görür. Dört çeşitleri vardır `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Bu yordam, en yaygın çeşitli olduğu `Sub Main()`. Daha fazla bilgi için bkz: [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Visual Basic sınırlamaları](../../../visual-basic/programming-guide/program-structure/limitations.md)
