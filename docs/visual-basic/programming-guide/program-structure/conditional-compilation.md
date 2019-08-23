---
title: Visual Basic'de Koşullu Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 1bee64568ff92468e29226a395f7e5335387e256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945580"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic'de Koşullu Derleme
*Koşullu derlemede*, bir programdaki belirli kod blokları, diğerleri gözardı edilirken seçime bağlı olarak derlenir.  
  
 Örneğin, farklı yaklaşımların hızını aynı programlama göreviyle karşılaştıran hata ayıklama deyimleri yazmak veya bir uygulamayı birden çok dil için yerelleştirmek isteyebilirsiniz. Koşullu derleme deyimleri, çalışma zamanında değil, derleme zamanı sırasında çalışacak şekilde tasarlanmıştır.  
  
 Kod bloklarını `#If...Then...#Else` yönergeyle koşullu olarak derlenebilecek şekilde belirtebilirsiniz. Örneğin, aynı kaynak koddan aynı uygulamanın Fransızca ve Almanca dil sürümlerini oluşturmak için, önceden tanımlanmış sabitleri `#If...Then` `FrenchVersion` ve `GermanVersion`kullanarak deyimlerde platforma özel kod kesimleri eklersiniz. Aşağıdaki örnek, aşağıdakilerin nasıl yapıldığını göstermektedir:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 `FrenchVersion` Koşullu derleme sabitinin değerini derleme zamanında olarak `True` ayarlarsanız, Fransızca sürümü için koşullu kod derlenir. `GermanVersion` Sabitin değerini olarak `True`ayarlarsanız, derleyici Almanca sürümünü kullanır. Hiçbiri olarak `True`ayarlanmazsa, son `Else` bloktaki kod çalıştırılır.  
  
> [!NOTE]
> Kod düzenlenirken otomatik tamamlama çalışmaz ve kod geçerli dalın bir parçası değilse koşullu derleme yönergeleri kullanılır.  
  
## <a name="declaring-conditional-compilation-constants"></a>Koşullu derleme sabitleri bildirme  
 Koşullu derleme sabitlerini üç şekilde ayarlayabilirsiniz:  
  
- **Proje tasarımcısında**  
  
- Komut satırı derleyicisini kullanırken komut satırında  
  
- Kodunuzda  
  
 Koşullu derleme sabitleri özel bir kapsama sahiptir ve standart koddan erişilemez. Koşullu derleme sabitinin kapsamı, ayarlandığı yönteme bağlıdır. Aşağıdaki tabloda, yukarıda bahsedilen üç yol kullanılarak bildirilen sabitlerin kapsamı listelenmektedir.  
  
|Sabit nasıl ayarlanır|Sabit kapsamı|  
|---|---|  
|**Proje Tasarımcısı**|Projedeki tüm dosyalar için ortak|  
|Komut satırı|Komut satırı derleyicisine geçirilen tüm dosyalar için ortak|  
|`#Const`koddaki ifade|Özel olarak bildirildiği dosya|  
  
|Proje tasarımcısında sabitleri ayarlamak için|  
|---|  
|-Yürütülebilir dosyanızı oluşturmadan önce, [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)bölümünde belirtilen adımları Izleyerek **Proje tasarımcısında** sabitler ayarlayın.|  
  
|Sabitleri komut satırında ayarlamak için|  
|---|  
|-Aşağıdaki örnekte gösterildiği gibi, koşullu derleme sabitleri girmek için **/d** anahtarını kullanın:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     **/D** anahtarı ve ilk sabit arasında boşluk gerekmez. Daha fazla bilgi için bkz. [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Komut satırı bildirimleri **Proje tasarımcısında**girilen bildirimleri geçersiz kılar, ancak onları silmez. **Proje tasarımcısında** ayarlanan bağımsız değişkenler sonraki derlemeler için geçerli olmaya devam eder.<br />     Koda sabitler yazarken, kendi kapsamları bildirildiği modülün tamamı olduğundan, kendi yerleşimine göre kesin bir kural yoktur.|  
  
|Kodunuzda sabitleri ayarlamak için|  
|---|  
|-Sabitleri, kullanıldıkları modülün bildirim bloğuna yerleştirin. Bu, kodunuzun düzenlenmesine ve okunmasını daha kolay tutmaya yardımcı olur.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|---|---|  
|[Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Kodunuzun okunmasını ve korunmasını kolaylaştırmak için öneriler sağlar.|  
  
## <a name="reference"></a>Başvuru  
 [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
