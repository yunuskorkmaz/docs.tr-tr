---
title: Salt Okunur Bağımlılık Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 256790880e6fcf3bd2492d3f3f00b532f6a31eea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568146"
---
# <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri
Bu konuda, var olan salt okunur bağımlılık özellikleri senaryoları ve özel salt okunur bağımlılık özelliği oluşturmaya yönelik teknikleri dahil olmak üzere, salt okunur bağımlılık özellikleri açıklanmaktadır.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu başlığı altında bağımlılık özelliği ve özel bağımlılık özelliği için meta verileri nasıl uygulanacağını uygulama temel senaryolar anladığınızı varsayar. Bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [bağımlılık özelliği meta verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) bağlamı için.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Varolan salt okunur bağımlılık özellikleri  
 Bazı tanımlanan bağımlılık özellikleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] framework salt okunurdur. Salt okunur bağımlılık özelliği belirtmek için normal durumu belirlenmesi için kullanılmalıdır, ancak burada bu duruma etkilenir çok çeşitli faktörler, ancak bu durum özelliğine gelen arzu değil yalnızca ayarı tarafından özellikleri bunlar nedeni bir kullanıcı arabirimi tasarımı açısından. Örneğin, özellik <xref:System.Windows.UIElement.IsMouseOver%2A> aslında fare girişinden belirlendiği durumudur. Bu değer true fare girişi atlayarak program üzerinden ayarlamak için her türlü girişim, öngörülemeyen olacaktır ve tutarsızlığa neden olabilir.  
  
 Salt okunur bağımlılık özellikleri ayarlanabilir olmaması sayesinde, birçok, bağımlılık özellikleri genellikle bir çözüm sunmak senaryoları için uygun olmayan (yani: veri bağlama, bir değer, doğrulama, animasyon, devralma doğrudan Stillenebilir). Ayarlanabilir, salt okunur bağımlılık olmasına rağmen özellikleri hala bazı özellik sistemindeki bağımlılık özellikleri tarafından desteklenen ek özellikleri vardır. En önemli kalan özellik salt okunur bağımlılık özelliği bir özellik tetikleyicisi stil olarak hala kullanılabilir yöneliktir. Normal Tetikleyicileri etkinleştirilemiyor [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliği; bir bağımlılık özelliği olması gerekir. Yukarıda sözü edilen <xref:System.Windows.UIElement.IsMouseOver%2A> özelliktir mükemmel bir yere olabilir bir stil denetimi için bazı yerlerde tanımlamak oldukça kullanışlı bir senaryo örneği bir arka plan, ön plan veya bileşik öğelerin içinde benzer özellikleri gibi visible özelliği Kullanıcı denetiminizin tanımlanan bazı bölgesini üzerine fare verdiğinde denetim değişecektir. Salt okunur bağımlılık özelliği değişiklikleri de algılanabilir ve özellik sisteminin doğal bir geçersiz kılma işlemleri tarafından bildirilen ve bu aslında özellik tetikleyicisi işlevselliğini dahili olarak destekler.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Özel salt okunur bağımlılık özellikleri oluşturma  
 Salt okunur bağımlılık özellikleri için birçok tipik bir bağımlılık özelliği senaryo neden çalışmaz ilgili yukarıdaki bölüme okuduğunuzdan emin olun. Ancak, uygun bir senaryoyu varsa, kendi salt okunur bağımlılık özelliği oluşturmak isteyebilirsiniz.  
  
 Salt okunur bağımlılık özelliği oluşturma işleminin açıklanan aynı mıdır [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [bağımlılık özelliği uygulama](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) konuları. Üç önemli farklar vardır:  
  
-   Özelliğinizi aramanızı <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> yöntemi yerine normal <xref:System.Windows.DependencyProperty.Register%2A> özelliği kayıt için yöntemi.  
  
-   Uygularken [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı" özelliği sarmalayıcı çok küme uygulaması yoktur, yani tutarsız ortak kapsayıcı için salt okunur durumda, kullanıma emin olun.  
  
-   Salt okunur kaydı tarafından döndürülen nesne <xref:System.Windows.DependencyPropertyKey> yerine <xref:System.Windows.DependencyProperty>. Bu alan üye olarak halen depolamanız gerekir, ancak genellikle, bu tür ortak üye yapacağınız değil.  
  
 Herhangi bir özel alan veya değer yedeklediğiniz Elbette, salt okunur bağımlılık özelliği için istediğinize karar mantığı kullanarak tam olarak yazılabilir. Ancak, özelliği başlangıçta veya çalışma zamanı mantığının parçası olarak ayarlamak için en kolay yolu özellik sisteminin kullanmaktır [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], özellik sistemi atlamak ve doğrudan özel yedekleme alanını ayarlamak yerine. Özellikle, bir imzası yok <xref:System.Windows.DependencyObject.SetValue%2A> türünde bir parametre kabul eden <xref:System.Windows.DependencyPropertyKey>. Nasıl ve nerede, bu değeri içinde uygulama mantığınızın programlanarak nasıl erişim ayarlamak isteyebilirsiniz etkiler <xref:System.Windows.DependencyPropertyKey> bağımlılık özelliği ilk kaydedildiğinde oluşturulur. Sınıf içindeki tüm bu mantığı işlemek, bunu özel bir duruma ya da derlemeyi diğer bölümlerinden ayarlanmış olması gerekiyorsa, bu iç ayarlayabilirsiniz. Bir yaklaşım ise çağrılacak <xref:System.Windows.DependencyObject.SetValue%2A> içinde saklanan özellik değerinin değiştirilmesi gereken bir sınıf örneğini bilgilendiren ilgili bir olayın olay işleyicisi sınıfı. Bağımlılık özellikleri eşleştirilmiş kullanarak birbirine bağlamak için başka bir yaklaşımdır <xref:System.Windows.PropertyChangedCallback> ve <xref:System.Windows.CoerceValueCallback> kayıt sırasında özelliklere meta veri parçası olarak geri çağırmalar.  
  
 Çünkü <xref:System.Windows.DependencyPropertyKey> özeldir ve dağıtılmadığı kodunuz dışında özellik sistemi tarafından salt okunur bağımlılık özelliği salt okunur bağımlılık özelliği iyi güvenlik ayarına sahip. Bir salt okunur bağımlılık özelliği için açık veya örtük olarak genel tanımlayıcı alan ve bu nedenle özelliği yaygın olarak ayarlanabilir. Daha fazla ayrıntı için bkz. [bağımlılık özelliği güvenliği](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
