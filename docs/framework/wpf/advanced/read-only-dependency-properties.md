---
title: Salt Okunur Bağımlılık Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 8adc90182f0f42f52e6ace4e13c68acb3539516b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187174"
---
# <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri
Bu konu, varolan salt okunur bağımlılık özellikleri ve özel salt okunur bağımlılık özelliği oluşturmak için senaryolar ve teknikler de dahil olmak üzere salt okunur bağımlılık özelliklerini açıklar.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliğini uygulamanın temel senaryolarını ve meta verilerin özel bağımlılık özelliğine nasıl uygulandığını anladığınızı varsayar. Bağlam için [Özel Bağımlılık Özellikleri](custom-dependency-properties.md) ve Bağımlılık Özelliği Meta [verilerine](dependency-property-metadata.md) bakın.  
  
<a name="existing"></a>
## <a name="existing-read-only-dependency-properties"></a>Varolan Salt Okunur Bağımlılık Özellikleri  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Çerçevede tanımlanan bağımlılık özelliklerinden bazıları salt okunur. Salt okunur bağımlılık özelliğini belirtmenin tipik nedeni, bunların durum belirleme için kullanılması gereken özellikler olması, ancak bu durum çok sayıda etkenin etkisi altında olması, ancak özelliği yalnızca bu duruma ayarlamanın kullanıcı arabirimi tasarım perspektifi. Örneğin, özellik <xref:System.Windows.UIElement.IsMouseOver%2A> gerçekten sadece fare girişi belirlenen durumu yüzey. Gerçek fare girişini atlatarak bu değeri programlı olarak ayarlamaya yönelik herhangi bir girişim öngörülemez olur ve tutarsızlığa neden olur.  
  
 Ayarlanamayan olması nedeniyle, yalnızca okuma bağımlılık özellikleri, bağımlılık özelliklerinin normalde bir çözüm sunduğu senaryoların çoğu için uygun değildir (yani: veri bağlama, doğrudan bir değere, doğrulamaya, animasyona, kalıtıma doğrulanabilir). Ayarlanamayan rağmen, salt okunur bağımlılık özellikleri, özellik sistemindeki bağımlılık özellikleri tarafından desteklenen bazı ek özelliklere sahiptir. Kalan en önemli özellik, salt okunur bağımlılık özelliğinin yine de bir stilde özellik tetikleyicisi olarak kullanılabilmedir. Normal ortak bir dil çalışma zamanı (CLR) özelliği olan tetikleyicileri etkinleştiremezsiniz; bir bağımlılık özelliği olması gerekir. Yukarıda belirtilen <xref:System.Windows.UIElement.IsMouseOver%2A> özellik, kullanıcı denetiminizin belirli bir bölgesinin üzerine fare yerleştirdiğinde, arka plan, ön plan veya denetim içindeki bileşik öğelerin benzer özellikleri gibi bazı görünür özelliklerin değişeceği bir denetim stilitanımlamanın oldukça yararlı olabileceği bir senaryonun mükemmel bir örneğidir. Salt okunur bağımlılık özelliğindeki değişiklikler de özellik sisteminin doğasında var olan geçersiz igeçersiz lik işlemleri tarafından algılanabilir ve raporlanabilir ve bu durum aslında özellik tetikleyici işlevselliğini dahili olarak destekler.  
  
<a name="new"></a>
## <a name="creating-custom-read-only-dependency-properties"></a>Özel Okuma-Salt Bağımlılık Özellikleri Oluşturma  
 Salt okunur bağımlılık özelliklerinin neden birçok tipik bağımlılık özelliği senaryosunda çalışmayamaz ile ilgili yukarıdaki bölümü okuduğunuzdan emin olun. Ancak uygun bir senaryonuz varsa, kendi salt okunur bağımlılık özelliğinizi oluşturmak isteyebilirsiniz.  
  
 Salt okunur bağımlılık özelliği oluşturma işleminin çoğu, [Özel Bağımlılık Özellikleri](custom-dependency-properties.md) ve Bağımlılık [Özelliği](how-to-implement-a-dependency-property.md) konuları nın uygulanmasında açıklandığı gibi aynıdır. Üç önemli fark vardır:  
  
- Mülkünüzü kaydederken, özellik <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> kaydı için <xref:System.Windows.DependencyProperty.Register%2A> normal yöntem yerine yöntemi arayın.  
  
- CLR "sarmalayıcı" özelliğini uygularken, sarmalayıcının da belirli bir uygulaması olmadığından emin olun, böylece açığa çıkardığınız genel sarıcı için salt okunur durumda tutarsızlık yoktur.  
  
- Salt okunur kaydıyla döndürülen <xref:System.Windows.DependencyPropertyKey> nesne <xref:System.Windows.DependencyProperty>yerine. Yine de bu alanı üye olarak saklamanız gerekir, ancak genellikle bu alanı bu tür bir genel üye yapmazsınız.  
  
 Salt okunur bağımlılık özelliğinizi destekleyen özel alan veya değer ne olursa olsun, karar verirseniz verin mantığınızı kullanarak elbette tamamen yazılabilir olabilir. Ancak, özelliği başlangıçta veya çalışma zamanı mantığının bir parçası olarak ayarlamanın en kolay yolu, özellik sistemini atlatmak ve özel destek alanını doğrudan ayarlamak yerine özellik sisteminin API'lerini kullanmaktır. Özellikle, türü <xref:System.Windows.DependencyObject.SetValue%2A> <xref:System.Windows.DependencyPropertyKey>bir parametre kabul eden bir imza vardır. Bu değeri uygulama mantığınızda programlı olarak nasıl ve nerede ayarladığınız, <xref:System.Windows.DependencyPropertyKey> bağımlılık özelliğini ilk kaydettirdiğinizde oluşturulan aerişe erişimi nasıl ayarlamak isteyebileceğinizi etkileyecektir. Bu mantığı sınıf içinde işlerseniz, özel hale getirebilirsiniz veya derlemenin diğer bölümlerinden ayarlanmasını isterseniz, bunu dahili olarak ayarlayabilirsiniz. Bir yaklaşım, <xref:System.Windows.DependencyObject.SetValue%2A> bir sınıf örneğini depolanan özellik değerinin değiştirilmesi gerektiğini bildiren ilgili bir olayın sınıf olay işleyicisini aramaktır. Başka bir yaklaşım, kayıt sırasında bu <xref:System.Windows.PropertyChangedCallback> özelliklerin meta verilerinin bir parçası olarak eşleştirilmiş ve <xref:System.Windows.CoerceValueCallback> geri aramaları kullanarak bağımlılık özelliklerini birbirine bağlamaktır.  
  
 Özel <xref:System.Windows.DependencyPropertyKey> olduğundan ve özellik sistemi tarafından kodunuzu dışında yayılmadığından, salt okunur bağımlılık özelliği, okuma yazma bağımlılık özelliğinden daha iyi ayar güvenliğine sahiptir. Okuma yazma bağımlılık özelliği için, tanımlama alanı açık veya örtülü olarak herkese açıktır ve böylece özellik yaygın olarak ayarlanabilir. Daha fazla ayrıntı için Bkz. [Bağımlılık Özelliği Güvenliği.](dependency-property-security.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
