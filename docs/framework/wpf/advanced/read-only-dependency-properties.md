---
title: "Salt Okunur Bağımlılık Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9cb4477fe388c294bbd6b87589d5a3108a90d27f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri
Bu konuda, varolan salt okunur bağımlılık özellikleri ve senaryoları ve özel salt okunur bağımlılık özelliği oluşturma tekniği de dahil olmak üzere, salt okunur bağımlılık özellikleri açıklanmaktadır.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bir bağımlılık özelliği ve meta verilerin özel bir bağımlılık özelliği için nasıl uygulanacağını uygulamanın temel senaryolarını anladığınızı varsayar. Bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) bağlamı için.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Varolan salt okunur bağımlılık özellikleri  
 Bazı tanımlanan bağımlılık özellikleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] framework salt okunur. Salt okunur bağımlılık özelliği belirtmek için normal durum belirlenmesi için kullanılmalıdır, ancak burada bu duruma etkileyen faktörler, ancak bu durumda özelliğine gelen arzu değil yalnızca ayarı çok sayıda tarafından özellikleri bunlar nedeni bir kullanıcı arabirimi tasarımı açısından. Örneğin, özellik <xref:System.Windows.UIElement.IsMouseOver%2A> gerçekten yalnızca fare girişinden belirlenen durumudur. Bu değer doğru fare girişini atlayarak programlı olarak ayarlamak için her türlü girişim öngörülemez olacaktır ve tutarsızlığa neden olabilir.  
  
 Salt okunur bağımlılık özellikleri ayarlanabilir olmaması sayesinde, birçok, bağımlılık özellikleri normalde bir çözüm sunar senaryoları için uygun olmayan (yani: veri bağlama, bir değer, doğrulama, animasyon, devralma doğrudan Stillenebilir). Ayarlanabilir, salt okunur bağımlılık olmasına rağmen özellikleri hala bazı özellik sistemindeki bağımlılık özellikleri tarafından desteklenen ek özelliklerine sahiptir. En önemli kalan salt okunur bağımlılık özelliği bir stil özelliğini tetikleyici olarak hala kullanılabilir bir özelliktir. Normal Tetikleyicileri etkinleştiremiyor [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özellik; bir bağımlılık özelliği olması gerekir. Daha önce bahsedilen <xref:System.Windows.UIElement.IsMouseOver%2A> özelliktir burada bunu olabilir bir denetim için bir stil bazı durumlarda tanımlamak oldukça yararlıdır senaryosu mükemmel bir örneği bir arka plan, ön plan veya içindeki bileşik öğelerin benzer özellikleri gibi görünür özelliği Kullanıcı tanımlı bazı denetiminizi bölge fare getirdiğinde denetim değiştirir. Salt okunur bağımlılık özelliği değişiklikleri de algılanabilir ve özellik sisteminin devralınan geçersiz kılma işlemleri tarafından bildirilen ve bu aslında özellik tetikleyici işlevselliğini dahili olarak destekler.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Özel salt okunur bağımlılık özellikleri oluşturma  
 Salt okunur bağımlılık özellikleri birçok Tipik bağımlılık özelliği senaryoları için neden çalışmaz ilgili yukarıdaki bölümü okuduğunuzdan emin olun. Ancak uygun bir senaryoyu varsa, kendi salt okunur bağımlılık özelliği oluşturmak isteyebilirsiniz.  
  
 Salt okunur bağımlılık özelliği oluşturma işleminin çoğunu açıklanan aynıdır [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [bağımlılık özelliği uygulama](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) Konular. Üç önemli farklılıklar vardır:  
  
-   Özelliğinizi kaydederken çağrısı <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> normal yerine yöntemi <xref:System.Windows.DependencyProperty.Register%2A> özellik kaydı için yöntem.  
  
-   Uygularken [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı" özelliğini sarmalayıcı çok kümesi uygulama yok, yani hiçbir tutarsızlık public sarmalayıcı için salt okunur durumda, kullanıma emin olun.  
  
-   Salt okunur kayıt tarafından döndürülen nesne <xref:System.Windows.DependencyPropertyKey> yerine <xref:System.Windows.DependencyProperty>. Bu alan üye olarak hala depolamanız gerekir, ancak genellikle, bu bir ortak üye türü yapacağınız değil.  
  
 Herhangi bir özel alan veya yedekleme değer salt okunur bağımlılık özelliğinizi Elbette karar mantığı kullanarak tam olarak yazılabilir olabilir. Ancak, başlangıçta veya çalışma zamanı mantığının parçası olarak özelliğini ayarlamak için en kolay yolu özellik sisteminin kullanmaktır [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], özellik sistemi atlamak ve özel yedekleme alanını doğrudan ayarlamak yerine. Özellikle, bir imzası yok <xref:System.Windows.DependencyObject.SetValue%2A> türünde bir parametre kabul eden <xref:System.Windows.DependencyPropertyKey>. Nasıl ve nerede, bu değer programlı olarak uygulamanızın mantığı içerisinde nasıl erişim ayarlamak isteyebilirsiniz etkiler <xref:System.Windows.DependencyPropertyKey> bağımlılık özelliği ilk kaydolurken oluşturulmuş. Sınıf içindeki tüm bu mantığı işlemek, bunu özel bir duruma ya da derlemeyi diğer bölümlerinden ayarlanması gerekiyorsa iç ayarlamanız. Bir yaklaşım ise çağırmak için <xref:System.Windows.DependencyObject.SetValue%2A> saklanan özellik değerinin değiştirilmesi gereken bir sınıf örneğini bilgilendiren ilgili bir olayın olay işleyicisi sınıfı içinde. Eşleştirilmiş kullanarak bağımlılık özellikleri birbirine bağlamak için başka bir yaklaşımdır <xref:System.Windows.PropertyChangedCallback> ve <xref:System.Windows.CoerceValueCallback> geri aramalar kayıt sırasında bu özelliklerin meta verilerinin bir parçası olarak.  
  
 Çünkü <xref:System.Windows.DependencyPropertyKey> özeldir ve dağıtılmadığı kodunuzu dışında özellik sistemi tarafından bir salt okunur bağımlılık özelliği okuma-yazma bağımlılık özelliğinden iyi güvenlik ayarına sahiptir. Bir okuma-yazma bağımlılık özelliği için tanımlayıcı alan açık veya örtülü olarak ortak ve böylece özelliği yaygın olarak ayarlanabilir. Daha fazla ayrıntı için bkz: [bağımlılık özelliği güvenlik](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
