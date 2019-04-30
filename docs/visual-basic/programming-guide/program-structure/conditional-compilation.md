---
title: Visual Basic'de Koşullu Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 828edf2e5491394f5ac802b5c9babfb3df359e59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758463"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic'de Koşullu Derleme
İçinde *koşullu derleme*, belirli bir programda kod bloklarının diğerleri göz ardı edilir ancak seçmeli olarak derlenir.  
  
 Örneğin, yazmak isteyebilirsiniz veya aynı programlama görevi farklı yaklaşımlara hızını karşılaştırma ifadeleri hata ayıklama birden çok dil için bir uygulamayı yerelleştirme getirmek isteyebilir. Koşullu derleme deyimleri, çalışma zamanında değil derleme zamanında çalışacak şekilde tasarlanmıştır.  
  
 İle koşullu olarak derlenmiş kod bloklarını belirtmek `#If...Then...#Else` yönergesi. Örneğin, Fransızca ve Almanca dil oluşturmak için aynı uygulama aynı sürümleri kaynak kodu, platforma özgü kod kesimlerinde ekleme `#If...Then` önceden tanımlı sabitler kullanılarak deyimleri `FrenchVersion` ve `GermanVersion`. Aşağıdaki örnek, gösterir nasıl:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 Değerini ayarlarsanız `FrenchVersion` koşullu derleme sabiti `True` derleme zamanında Fransızca sürümü için koşullu kod derlenir. Değerini ayarlarsanız `GermanVersion` için sabit `True`, derleyici Almanca sürümü kullanır. Hiçbiri ayarlanırsa `True`, son kodda `Else` bloğu çalışır.  
  
> [!NOTE]
>  Otomatik Tamamlama düzenleme kodlarken not işlevi ve kodun geçerli dal parçası değilse, koşullu derleme yönergeleri kullanarak olur.  
  
## <a name="declaring-conditional-compilation-constants"></a>Koşullu derleme Sabitleri Bildirme  
 Koşullu derleme sabitleri üç yoldan biriyle ayarlayabilirsiniz:  
  
- İçinde **Proje Tasarımcısı**  
  
- Komut satırı derleyicisini kullanarak komut satırında  
  
- Kodunuzda  
  
 Koşullu derleme sabitleri, özel bir kapsama sahip ve standart koddan erişilemez. Koşullu derleme sabiti kapsamı ayarlanmış şekilde bağlıdır. Aşağıdaki tabloda her yukarıda açıklanan üç yoldan birini kullanarak bildirilen sabitlerin kapsamı listeler.  
  
|Sabiti nasıl ayarlanır|Sabit kapsam|  
|---|---|  
|**Proje Tasarımcısı**|Projedeki tüm dosyalara genel|  
|Komut satırı|Komut satırı derleyiciye tüm dosyalara genel|  
|`#Const` koddaki bildirimi|İçinde bildirildiği dosyanın özel|  
  
|Proje Tasarımcısı'nda sabitleri ayarlamak için|  
|---|  
|-Sabitler, yürütülebilir dosya oluşturma önce kümesinde **Proje Tasarımcısı** içinde sağlanan adımları izleyerek [yönetme proje ve çözüm özelliklerini](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Komut satırında sabitleri ayarlamak için|  
|---|  
|-Kullanma **/d** geçme aşağıdaki örnekte olduğu gibi koşullu derleme sabitleri girin:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Arasında boşluk gereklidir **/d** anahtar ve ilk sabiti. Daha fazla bilgi için [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Komut satırı bildirimleri geçersiz kılma bildirimi girilen **Proje Tasarımcısı**, ancak bunları silme. Bağımsız değişkenler kümesinde **Proje Tasarımcısı** sonraki derleme için yürürlükte kalır.<br />     Sabitler kodda yazarken, hiçbir katı kurallar vardır, yerleştirme için kendi kapsamı içinde bildirildikleri tüm modül olduğundan.|  
  
|Kodunuzda sabitleri ayarlamak için|  
|---|  
|-Sabitleri bunlar kullanılır modül bildirimi bloğunda yerleştirin. Bu, kodunuzu düzenli ve okunması kolay tutmaya yardımcı olur.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|---|---|  
|[Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Kodunuzu okunması ve düzenlenmesi daha kolay yapmak için öneriler sağlar.|  
  
## <a name="reference"></a>Başvuru  
 [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
