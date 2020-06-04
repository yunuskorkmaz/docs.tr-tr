---
title: Bir Visual Basic Programının Yapısı
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: dc6b38d78f02a42c8e7cc2aa964e9f3f74996f44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408770"
---
# <a name="structure-of-a-visual-basic-program"></a>Bir Visual Basic Programının Yapısı
Bir Visual Basic program standart yapı taşlarından oluşturulmuştur. Bir *çözüm* bir veya daha fazla projeden oluşur. Sırasıyla bir *Proje* , bir veya daha fazla derleme içerebilir. Her *derleme* bir veya daha fazla kaynak dosyasından derlenir. *Kaynak dosya* , sonunda tüm kodunuzu içeren sınıfların, yapıların, modüllerin ve arabirimlerin tanımını ve uygulamasını sağlar.  
  
 Visual Basic bir programın bu yapı taşları hakkında daha fazla bilgi için bkz. [.net 'Teki](../../../standard/assembly/index.md) [çözümler ve projeler](/visualstudio/ide/solutions-and-projects-in-visual-studio) ve derlemeler.  
  
## <a name="file-level-programming-elements"></a>Dosya düzeyi programlama öğeleri  
 Bir proje veya dosya başlattığınızda ve kod düzenleyicisini açtığınızda, bazı kodları zaten yerinde ve doğru sırada görürsünüz. Yazdığınız herhangi bir kod aşağıdaki sırayı izlemelidir:  
  
1. `Option`deyimler  
  
2. `Imports`deyimler  
  
3. `Namespace`deyimler ve isim uzayı düzeyi öğeleri  
  
 Deyimleri farklı bir sırada girerseniz, derleme hataları oluşabilir.  
  
 Bir program, koşullu derleme deyimleri de içerebilir. Bunları kaynak dosyada, önceki sıranın deyimleri arasında birbirine bağlayabilirsiniz.  
  
### <a name="option-statements"></a>Seçenek deyimleri  
 `Option`deyimler sonraki kod için zemin kuralları oluştururlar ve söz dizimi ve mantık hatalarını önlemeye yardımcı olur. [Açık Ifade seçeneği](../../language-reference/statements/option-explicit-statement.md) , tüm değişkenlerin doğru şekilde bildirilmesini ve doğru yazıldığını sağlar ve bu da hata ayıklama süresini azaltır. [Strict deyimleri](../../language-reference/statements/option-strict-statement.md) , farklı veri türleri değişkenleri arasında çalışırken gerçekleşebileceği mantık hatalarını ve veri kaybını en aza indirmenize yardımcı olur. [Option Compare deyimleri](../../language-reference/statements/option-compare-statement.md) , dizelerin birbirlerine veya değerlerine göre birbirleriyle karşılaştırılacağı yöntemi belirtir `Binary` `Text` .  
  
### <a name="imports-statements"></a>Imports deyimleri  
 Projenizin dışında tanımlanan adları içeri aktarmak için [Imports (.net ad alanı ve türü) ifadesini](../../language-reference/statements/imports-statement-net-namespace-and-type.md) dahil edebilirsiniz. Bir `Imports` ifade, kodunuzun sınıflara ve içeri aktarılan ad alanında tanımlanan diğer türlere, bunları nitelendirmek gerekmeden başvurmasını sağlar. `Imports`Uygun şekilde çok sayıda deyim kullanabilirsiniz. Daha fazla bilgi için bkz. [Başvurular ve Imports ekstresi](references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Namespace deyimleri  
 Ad alanları, gruplama ve erişim kolaylığı için programlama öğelerinizi düzenlemenize ve sınıflandırmanıza yardımcı olur. Belirli bir ad alanı içinde aşağıdaki deyimleri sınıflandırmak için [Namespace deyimini](../../language-reference/statements/namespace-statement.md) kullanın. Daha fazla bilgi için bkz. [Visual Basic ad alanları](namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Koşullu derleme deyimleri  
 Koşullu derleme deyimleri, kaynak dosyanızda neredeyse her yerde görünebilir. Bunlar, belirli koşullara bağlı olarak, kodunuzun bölümlerinin derleme zamanına dahil edilmesini veya dışlanmasına neden olur. Koşullu kod yalnızca hata ayıklama modunda çalıştığı için, bunları uygulamanızda hata ayıklamak için de kullanabilirsiniz. Daha fazla bilgi için bkz. [koşullu derleme](conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Ad alanı düzeyinde programlama öğeleri  
 Sınıflar, yapılar ve modüller, kaynak dosyanızdaki tüm kodu içerir. Ad alanı *düzeyindeki* öğelerdir ve bu, bir ad alanı içinde veya kaynak dosya düzeyinde görünebilir. Diğer tüm programlama öğelerinin bildirimlerini tutar. Öğe imzalarını tanımlayan ancak uygulama sağlamayan arabirimler, modül düzeyinde de görünür. Modül düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:  
  
- [Class Deyimi](../../language-reference/statements/class-statement.md)  
  
- [Structure Yapısı](../../language-reference/statements/structure-statement.md)  
  
- [Module Deyimi](../../language-reference/statements/module-statement.md)  
  
- [Interface Deyimi](../../language-reference/statements/interface-statement.md)  
  
 Ad alanı düzeyindeki veri öğeleri numaralandırmalar ve temsilcileriniz.  
  
## <a name="module-level-programming-elements"></a>Modül düzeyinde programlama öğeleri  
 İşlemler, işleçler, Özellikler ve olaylar çalıştırılabilir kodu tutabilecek tek programlama öğeleridir (çalışma zamanında eylem gerçekleştiren deyimler). Programınızın *Modül düzeyi* öğeleridir. Yordam düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:  
  
- [Function Deyimi](../../language-reference/statements/function-statement.md)  
  
- [Sub Deyimi](../../language-reference/statements/sub-statement.md)  
  
- [Declare Deyimi](../../language-reference/statements/declare-statement.md)  
  
- [Operator Deyimi](../../language-reference/statements/operator-statement.md)  
  
- [Property Deyimi](../../language-reference/statements/property-statement.md)  
  
- [Event Deyimi](../../language-reference/statements/event-statement.md)  
  
 Modül düzeyindeki veri öğeleri, değişkenler, sabitler, numaralandırmalar ve temsilcilerle.  
  
## <a name="procedure-level-programming-elements"></a>Yordam düzeyi programlama öğeleri  
 *Yordam düzeyindeki* öğelerin çoğu, programınızın çalışma zamanı kodunu oluşturan çalıştırılabilir deyimlerdir. Tüm yürütülebilir kodlar bazı yordamda ( `Function` , `Sub` ,,,, `Operator` `Get` `Set` `AddHandler` , `RemoveHandler` , `RaiseEvent` ,,,,) olmalıdır. Daha fazla bilgi için bkz. [deyimler](../language-features/statements.md).  
  
 Yordam düzeyindeki veri öğeleri yerel değişkenlerle ve sabitler ile sınırlıdır.  
  
## <a name="the-main-procedure"></a>Ana yordam  
 `Main`Yordam, uygulamanız yüklendiğinde çalıştırılacak ilk koddur. `Main`, uygulamanız için başlangıç noktası ve genel denetim olarak görev yapar. Dört değişken vardır `Main` :  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Bu yordamın en yaygın çeşitliliği şunlardır `Sub Main()` . Daha fazla bilgi için bkz. [Visual Basic ana yordam](main-procedure.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Ana Yordam](main-procedure.md)
- [Visual Basic Adlandırma Kuralları](naming-conventions.md)
- [Visual Basic Sınırlamaları](limitations.md)
