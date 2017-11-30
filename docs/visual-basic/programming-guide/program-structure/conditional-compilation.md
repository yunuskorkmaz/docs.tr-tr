---
title: "Visual Basic'de Koşullu Derleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 559380dc9baceb2fba4dca782e83f335f1bcd92d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic'de Koşullu Derleme
İçinde *koşullu derleme*, belirli bir programı kod bloklarını diğerleri yoksayılır sırada seçmeli olarak derlenir.  
  
 Örneğin, yazmak isteyebilirsiniz aynı programlama görev veya farklı yaklaşımlara hızını karşılaştırma ifadeleri hata ayıklama bir uygulama için birden çok dilde yerelleştirme isteyebilir. Koşullu derleme deyimleri, çalışma zamanında derleme süresi sırasında çalışmak üzere tasarlanmıştır.  
  
 İle koşullu derlenmiş kod bloklarını belirtmek `#If...Then...#Else` yönergesi. Örneğin, Fransızca ve Almanca dil oluşturmak için aynı uygulama aynı sürümlerini kaynak kodu, platforma özgü kod kesimlerinde katıştırmak `#If...Then` önceden tanımlanmış sabitleri using deyimleri `FrenchVersion` ve `GermanVersion`. Aşağıdaki örnekte gösterilmiştir nasıl:  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 Değerini ayarlarsanız `FrenchVersion` koşullu derleme sabiti `True` derleme zamanında Fransızca sürümü koşullu kodunu derlenir. Değerini ayarlarsanız `GermanVersion` için sabit `True`, Almanca sürümü derleyici kullanır. Hiçbiri ayarlanmışsa `True`, son kodda `Else` engelleme çalıştırır.  
  
> [!NOTE]
>  Otomatik Tamamlama düzenleme kodlarken çalışmamasına ve kod geçerli dalı parçası değilse, koşullu derleme yönergeleri kullanarak olur.  
  
## <a name="declaring-conditional-compilation-constants"></a>Koşullu derleme Sabitleri Bildirme  
 Koşullu derleme sabitleri üç şekilde ayarlayabilirsiniz:  
  
-   İçinde **Proje Tasarımcısı**  
  
-   Komut satırı derleyicisi kullanırken komut satırında  
  
-   Kodunuzda  
  
 Koşullu derleme sabitleri özel bir kapsama sahip ve standart koddan erişilemez. Koşullu derleme sabiti kapsamını ayarlandı yolda bağlıdır. Aşağıdaki tabloda her yukarıdaki üç yolla kullanılarak bildirilen sabitleri kapsamını listeler.  
  
|Sabiti nasıl ayarlanır|Kapsamı sabiti|  
|---|---|  
|**Proje Tasarımcısı**|Projedeki tüm dosyalar için genel|  
|Komut satırı|Komut satırı derleyicisi geçirilen tüm dosyalara genel|  
|`#Const`kodda deyimi|İçinde bildirilmiş dosyasına özel|  
  
|Proje Tasarımcısı'nda sabitleri ayarlamak için|  
|---|  
|-Sabitler yürütülebilir dosyanızı oluşturma önce kümesinde **Proje Tasarımcısı** içinde sağlanan adımları izleyerek [yönetme proje ve çözüm özelliklerini](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Komut satırında sabitleri ayarlamak için|  
|---|  
|-Kullanın **/d** anahtar aşağıdaki örnekteki gibi koşullu derleme sabitleri girin:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Arasında boşluk gereklidir **/d** anahtarı ve ilk sabiti. Daha fazla bilgi için bkz: [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Komut satırı bildirimleri geçersiz kılma girilen bildirimleri **Proje Tasarımcısı**, ancak bunları silme değil. Bağımsız değişkenler kümesinde **Proje Tasarımcısı** sonraki derlemeler için yürürlükte kalır.<br />     Sabitler kodda yazarken, katı kural yok onların yerini aldığını kapsamlarına bildirilen tüm modülü olduğundan.|  
  
|Kodunuzda sabitleri ayarlamak için|  
|---|  
|-Sabitleri kullanılacak modülünü bildirimi bloğunda yerleştirin. Bu, kodunuzu düzenli ve kolay okunur tutmaya yardımcı olur.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|---|---|  
|[Program yapısı ve kod kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Kodunuzu okuyun ve sürdürmek daha kolay yapmak için öneriler sağlar.|  
  
## <a name="reference"></a>Başvuru  
 [#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
