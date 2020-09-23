---
title: Koşullu Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e59296882edc018259816c73b6ae861b3b296783
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098975"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic'de Koşullu Derleme

*Koşullu derlemede*, bir programdaki belirli kod blokları, diğerleri gözardı edilirken seçime bağlı olarak derlenir.  
  
 Örneğin, farklı yaklaşımların hızını aynı programlama göreviyle karşılaştıran hata ayıklama deyimleri yazmak veya bir uygulamayı birden çok dil için yerelleştirmek isteyebilirsiniz. Koşullu derleme deyimleri, çalışma zamanında değil, derleme zamanı sırasında çalışacak şekilde tasarlanmıştır.  
  
 Kod bloklarını yönergeyle koşullu olarak derlenebilecek şekilde belirtebilirsiniz `#If...Then...#Else` . Örneğin, aynı kaynak koddan aynı uygulamanın Fransızca ve Almanca dil sürümlerini oluşturmak için, `#If...Then` önceden tanımlanmış sabitleri ve kullanarak deyimlerde platforma özel kod kesimleri eklersiniz `FrenchVersion` `GermanVersion` . Aşağıdaki örnek, aşağıdakilerin nasıl yapıldığını göstermektedir:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 `FrenchVersion`Koşullu derleme sabitinin değerini `True` derleme zamanında olarak ayarlarsanız, Fransızca sürümü için koşullu kod derlenir. `GermanVersion`Sabitin değerini olarak ayarlarsanız `True` , derleyici Almanca sürümünü kullanır. Hiçbiri olarak ayarlanmazsa `True` , son `Else` bloktaki kod çalıştırılır.  
  
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
|`#Const` koddaki ifade|Özel olarak bildirildiği dosya|  
  
|Proje tasarımcısında sabitleri ayarlamak için|  
|---|  
|-Yürütülebilir dosyanızı oluşturmadan önce, [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)bölümünde belirtilen adımları Izleyerek **Proje tasarımcısında** sabitler ayarlayın.|  
  
|Sabitleri komut satırında ayarlamak için|  
|---|  
|-Aşağıdaki örnekte gösterildiği gibi, koşullu derleme sabitleri girmek için **-d** anahtarını kullanın:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     **-D** anahtarı ve ilk sabit arasında boşluk gerekmez. Daha fazla bilgi için bkz. [-tanımlama (Visual Basic)](../../reference/command-line-compiler/define.md).<br />     Komut satırı bildirimleri **Proje tasarımcısında**girilen bildirimleri geçersiz kılar, ancak onları silmez. **Proje tasarımcısında** ayarlanan bağımsız değişkenler sonraki derlemeler için geçerli olmaya devam eder.<br />     Koda sabitler yazarken, kendi kapsamları bildirildiği modülün tamamı olduğundan, kendi yerleşimine göre kesin bir kural yoktur.|  
  
|Kodunuzda sabitleri ayarlamak için|  
|---|  
|-Sabitleri, kullanıldıkları modülün bildirim bloğuna yerleştirin. Bu, kodunuzun düzenlenmesine ve okunmasını daha kolay tutmaya yardımcı olur.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|---|---|  
|[Program yapısı ve kod kuralları](program-structure-and-code-conventions.md)|Kodunuzun okunmasını ve korunmasını kolaylaştırmak için öneriler sağlar.|  
  
## <a name="reference"></a>Başvuru  

 [#Const Yönergesi](../../language-reference/directives/const-directive.md)  
  
 [#If... Sonra... #Else yönergeler](../../language-reference/directives/if-then-else-directives.md)  
  
 [-tanımla (Visual Basic)](../../reference/command-line-compiler/define.md)
