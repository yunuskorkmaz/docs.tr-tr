---
title: Salt Okunur Bağımlılık Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: a849b835bab832a4ddb8d594d1788ab062f4284e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459011"
---
# <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri
Bu konu, mevcut salt okuma bağımlılığı özellikleri ve özel salt okunurdur bir bağımlılık özelliği oluşturmaya yönelik senaryolar ve teknikler dahil salt okuma bağımlılığı özelliklerini açıklar.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konu, bağımlılık özelliği uygulama ve meta verilerin özel bir bağımlılık özelliğine uygulanma şeklini anladığınızı varsayar. Bağlam için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md) ve [bağımlılık özelliği meta verileri](dependency-property-metadata.md) .  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Mevcut salt okunurdur bağımlılık özellikleri  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çerçevesinde tanımlanan bağımlılık özelliklerinden bazıları salt okunurdur. Salt okunurdur bir bağımlılık özelliği belirtmenin tipik nedeni, bunların durum belirleme için kullanılması gereken özellikler olduğundan, bu durumun çok sayıda faktörden etkilenmesinden, ancak özelliğin bu duruma Kullanıcı arabirimi tasarım perspektifi. Örneğin, <xref:System.Windows.UIElement.IsMouseOver%2A> özellik, fare girişinden belirlendiği gibi oldukça yalnızca ortaya çıkmış durumda olur. Bu değeri, doğru fare girişinin bir atlama yöntemiyle programlı bir şekilde ayarlama girişimleri tahmin edilemez ve tutarsızlığa neden olabilir.  
  
 Özelliği ayarlanamaz olan sanallaştırmadan, salt okuma bağımlılığı özellikleri, bağımlılık özelliklerinin normalde çözüm sunduğu birçok senaryoya uygun değildir (yani, veri bağlama, doğrudan bir değere, doğrulamaya, animasyona, devralmaya göre Stillenebilir). Ayarlanamaz olsa da, salt okuma bağımlılığı özellikleri hala Özellik sisteminde bağımlılık özellikleri tarafından desteklenen ek özelliklerin bazılarına sahiptir. En önemli geri kalan özellik, salt okunurdur ve bir stilde özellik tetikleyicisi olarak kullanılmaya devam edilebilir. Normal bir ortak dil çalışma zamanı (CLR) özelliği ile Tetikleyicileri etkinleştiremezsiniz; bağımlılık özelliği olması gerekir. En çok bahsedilen <xref:System.Windows.UIElement.IsMouseOver%2A> özelliği, bir denetimin stil tanımlamak için oldukça yararlı olabilecek bir senaryoya yönelik kusursuz bir örnektir. Bu, arka plan, ön plan veya denetim içindeki bileşik öğelerin benzer özellikleri gibi bazı görünür Özellikler Kullanıcı denetiminizin bazı tanımlı bölgelerine bir fare yerleştirdiği zaman değiştirin. Salt okunurdur bir bağımlılık özelliğindeki değişiklikler özellik sisteminin devralınan geçersiz kılma işlemlerine göre algılanır ve bildirilebilir ve bu özellik, özellik tetikleyici işlevselliğini dahili olarak destekler.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Özel salt okuma bağımlılığı özellikleri oluşturma  
 Yalnızca okuma bağımlılığı özelliklerinin çoğu tipik bağımlılık özelliği senaryosunda çalışmadığına ilişkin yukarıdaki bölümü okuduğunuzdan emin olun. Ancak uygun bir senaryonuz varsa, kendi salt okunurdur.  
  
 Salt okunurdur bir bağımlılık özelliği oluşturma işleminin büyük bölümü, [Özel bağımlılık özelliklerinde](custom-dependency-properties.md) açıklananla aynıdır ve [bir bağımlılık özelliği konuları uygular](how-to-implement-a-dependency-property.md) . Üç önemli fark vardır:  
  
- Özelliği kaydederken, özellik kaydı için normal <xref:System.Windows.DependencyProperty.Register%2A> yöntemi yerine <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> yöntemini çağırın.  
  
- CLR "sarmalayıcı" özelliğini uygularken, sarmalayıcının bir küme uygulamasına sahip olmadığından emin olun. böylece, seçtiğiniz ortak sarmalayıcı için salt okuma durumunda bir tutarsızlık olmaz.  
  
- Salt okuma kaydı tarafından döndürülen nesne <xref:System.Windows.DependencyProperty>yerine <xref:System.Windows.DependencyPropertyKey>. Bu alanı yine de üye olarak depolamanız gerekir, ancak genellikle türün genel bir üyesini yapmamalıdır.  
  
 Yalnızca okuma bağımlılığı özelliğini yedeklediğiniz özel alan veya değer, karar vereceğiniz mantığı kullanarak tamamen yazılabilir olabilir. Ancak, özelliği başlangıçta veya çalışma zamanı mantığının bir parçası olarak ayarlamanın en kolay yolu, özellik sistemini atlamaktansa ve özel destek alanını doğrudan ayarlayarak özellik sisteminin API 'Lerini kullanmaktır. Özellikle, <xref:System.Windows.DependencyPropertyKey>türünde bir parametre kabul eden <xref:System.Windows.DependencyObject.SetValue%2A> imzası vardır. Uygulama mantığınızın içindeki bu değeri programlı bir şekilde nasıl ayarlayabileceğiniz, bağımlılık özelliğini ilk kez kaydettiğinizde oluşturulan <xref:System.Windows.DependencyPropertyKey> erişimi nasıl ayarlamak istediğinizi etkiler. Bu mantığı tüm sınıf içinde işleyebilir, bunu özel hale getirebilirsiniz veya derlemenin diğer bölümlerinden ayarlanmak istiyorsanız içsel olarak ayarlayabilirsiniz. Bir yaklaşım, saklı Özellik değerinin değiştirilmesi gerektiğini bir sınıf örneğine bildiren ilgili bir olayın sınıf olay işleyicisi içinde <xref:System.Windows.DependencyObject.SetValue%2A> çağırmasıdır. Başka bir yaklaşım de, kayıt sırasında bu özelliklerin meta verilerinin bir parçası olarak eşleştirilmiş <xref:System.Windows.PropertyChangedCallback> ve <xref:System.Windows.CoerceValueCallback> geri çağırmaları kullanarak bağımlılık özelliklerini birbirine bağlamaktır.  
  
 <xref:System.Windows.DependencyPropertyKey> özel olduğundan ve kodunuzun dışında özellik sistemi tarafından yayılmadığından, salt okunurdur, salt okunurdur bir Read-Write bağımlılık özelliğinden daha iyi ayar güvenliği vardır. Okuma-yazma bağımlılığı özelliği için, tanımlayıcı alan açık veya örtük olarak genel olur ve bu nedenle Özellik yaygın olarak ayarlanabilir. Daha fazla bilgi için bkz. [bağımlılık özelliği güvenliği](dependency-property-security.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
