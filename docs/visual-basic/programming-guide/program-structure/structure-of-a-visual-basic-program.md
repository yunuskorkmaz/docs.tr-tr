---
title: Bir Visual Basic Programının Yapısı
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: daaafa4877e9fc5abd7e720c5a91aa61f24a686c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686055"
---
# <a name="structure-of-a-visual-basic-program"></a>Bir Visual Basic Programının Yapısı
Bir Visual Basic programını standart yapı taşlarından oluşturulmuştur. A *çözüm* bir veya daha fazla proje içerir. A *proje* sırayla bir veya daha fazla içerebilir. Her *derleme* bir veya daha fazla kaynak dosyalarından derlenir. A *kaynak dosyası* tanımı ve sınıflar, yapılar, modülleri ve sonuç olarak, kodunuzu içeren arabirimleri uygulamasını sağlar.  
  
 Bir Visual Basic programını bu yapı taşları hakkında daha fazla bilgi için bkz. [çözümler ve projeler](/visualstudio/ide/solutions-and-projects-in-visual-studio) ve [derlemeler ve genel derleme önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
## <a name="file-level-programming-elements"></a>Dosya düzeyinde programlama öğeleri  
 Bir proje veya dosya başlatma ve Kod Düzenleyicisi'ni açın, bazı kodlar zaten yerinde ve doğru sırada bakın. Yazdığınız kod, aşağıdaki sırayı izlemelidir:  
  
1.  `Option` Deyimleri  
  
2.  `Imports` Deyimleri  
  
3.  `Namespace` ifadeler ve ad alanı düzeyinde öğeleri  
  
 Farklı bir sırada deyimleri girerseniz, derleme hatalarıyla sonuçlanabilir.  
  
 Bir program, koşullu derleme deyimleriyle de içerebilir. Bu kaynak dosyadaki önceki dizisi deyimleri arasında aralarına koyabilirsiniz.  
  
### <a name="option-statements"></a>Seçenek deyimleri  
 `Option` deyimlerini izleyen kod, sözdizimi ve mantık hatalarını engellemeye yardımcı olmak için çığır kuralları oluşturun. [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md) tüm değişkenleri bildirilir ve doğru yazıldığından, hata ayıklama zaman azaltan sağlar. [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) arasında farklı veri türlerinin değişkenleri çalışırken oluşabilecek mantık hataları ve veri kaybını en aza indirmek için yardımcı olur. [Seçenek karşılaştırma ifadesini](../../../visual-basic/language-reference/statements/option-compare-statement.md) şekilde dizeleri, birbiriyle bağlı karşılaştırılır belirtir, `Binary` veya `Text` değerleri.  
  
### <a name="imports-statements"></a>İçeri aktarmalar deyimleri  
 Dahil edebilirsiniz bir [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) projenizin dışında tanımlı adları almak için. Bir `Imports` deyimi sınıfları ve bunları uygun gerek kalmadan içeri aktarılan ad alanı içinde tanımlanan diğer türleri başvurmak kodunuzu sağlar. Kadar kullanabileceğiniz `Imports` deyimleri uygun şekilde. Daha fazla bilgi için [References ve Imports deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Namespace deyimleri  
 Düzenlemek ve programlama öğeleriniz için gruplandırma ve Erişim Kolaylığı sınıflandırma ad alanları yardımcı olur. Kullandığınız [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md) belirli bir ad alanı içinde aşağıdaki deyimleri sınıflandırmak için. Daha fazla bilgi için [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Koşullu derleme deyimleri  
 Koşullu derleme deyimleri, neredeyse her yerden, kaynak dosyada görünebilir. Bunlar, kodunuzun dahil edilecek veya hariç belirli koşullara bağlı olarak derleme zamanında bölümlerini neden. Koşullu kodu hata ayıklama modu yalnızca içinde çalıştığı için Ayrıca bunları, uygulamanızı hata ayıklama için kullanabilirsiniz. Daha fazla bilgi için [koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Namespace düzeyi programlama öğeleri  
 Sınıflar, yapılar ve modüller, kaynak dosyanızdaki tüm kod içerir. Bunlar *ad alanı düzeyinde* öğeleri, bir ad alanındaki veya kaynak dosya düzeyinde görünebilir. Bunlar, diğer programlama öğeleri bildirimlerini basılı tutun. Öğe imzaları tanımlayın, ancak herhangi bir uygulama sağlamak, arabirimler, Modül düzeyinde de görünür. Modül düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:  
  
-   [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Verileri ad alanı düzeyinde sabit listeleri ve temsilciler öğeleridir.  
  
## <a name="module-level-programming-elements"></a>Modül düzeyi programlama öğeleri  
 Yordamları, işleçler, özellikler ve olaylar yürütülebilir kod (çalışma zamanında işlemleri deyimleri) içerebileceği yalnızca programlama öğelerdir. Bunlar *Modül düzeyinde* , programınızın öğeleri. Yordam düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:  
  
-   [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Veri Modül düzeyinde değişkenleri, sabitleri, sabit listeleri ve temsilciler öğeleridir.  
  
## <a name="procedure-level-programming-elements"></a>Yordam düzeyi programlama öğeleri  
 Çoğu içeriğinin *yordam düzeyi* programınızın çalışma zamanı koduyla oluşturan yürütülebilir deyimleri öğeleridir. Tüm yürütülebilir kod bazı yordamda olmalıdır (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Daha fazla bilgi için [deyimleri](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Veri öğeleri yordamı düzeyinde, yerel değişkenleri ve sabitleri için sınırlıdır.  
  
## <a name="the-main-procedure"></a>Main yordamı  
 `Main` Yordamı uygulamanız yüklendiğinde çalıştırmak için ilk kodu verilmiştir. `Main` Uygulamanız için genel denetim ve başlangıç noktası olarak görev yapar. Dört çeşitleri vardır `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Bu yordam en sık kullanılan çeşitli olan `Sub Main()`. Daha fazla bilgi için [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Visual Basic sınırlamaları](../../../visual-basic/programming-guide/program-structure/limitations.md)
