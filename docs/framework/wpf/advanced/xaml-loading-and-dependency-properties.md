---
title: XAML Yükleme ve Bağımlılık Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: de8050e582f5b1a5a288c350c179cfa24fb5471c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186247"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML Yükleme ve Bağımlılık Özellikleri
[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] İşlemcinin geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması doğal olarak bağımlılık özelliği farkındadır. İşlemci, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ikili [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve bağımlılık özellikleri olan işleme öznitelikleri yüklerken bağımlılık özellikleri için özellik sistemi yöntemlerini kullanır. Bu özellik sarmalayıcıları etkili bir şekilde atlar. Özel bağımlılık özelliklerini uyguladığınızda, bu davranışı hesaba katmalısınız ve özellik sistem yöntemleri <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A>.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliklerini hem tüketici hem de yazar olarak anladığınızı ve [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md) ve Özel Bağımlılık [Özellikleri'ni](custom-dependency-properties.md)okuduğunuzu varsayar. [Ayrıca XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) ve [XAML Sözdizimi Ayrıntılı](xaml-syntax-in-detail.md)olarak okumuş olmalıdır.  
  
<a name="implementation"></a>
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML Yükleyici Uygulaması ve Performansı  
 Uygulama nedenleriyle, bir özelliği bağımlılık özelliği olarak tanımlamak ve özellik sarıcısını <xref:System.Windows.DependencyObject.SetValue%2A> ve ayarlayıcısını kullanmak yerine onu ayarlamak için özellik sistemi yöntemine erişmek hesaplama olarak daha ucuzdur. Bunun nedeni, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir işlemcinin yalnızca biçimlendirmenin yapısı ve çeşitli dizeleri ile gösterilen tür ve üye ilişkilerini bilmeye dayalı olarak destek kodunun tüm nesne modelini çıkarması gerektiğidir.  
  
 Tür xmlns ve derleme öznitelikleri bir arada bakılır, ancak üyeleri tanımlayan, hangi bir öznitelik olarak ayarlanması destekleyebilir belirleme ve özellik <xref:System.Reflection.PropertyInfo>değerleri desteği aksi takdirde kullanarak geniş yansıma gerektirecektir türleri çözme . Belirli bir türdeki bağımlılık özellikleri özellik sistemi üzerinden bir depolama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tablosu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak erişilebilir olduğundan, işlemcisinin uygulanması bu tabloyu kullanır ve <xref:System.Windows.DependencyObject.SetValue%2A> herhangi bir <xref:System.Windows.DependencyObject> özellik *ABC'nin,* bağımlılık özelliği tanımlayıcısı *ABCProperty'i*kullanarak, türemiş türü arayarak daha verimli bir şekilde ayarlanabileceği çıkarımını sağlar.  
  
<a name="implications"></a>
## <a name="implications-for-custom-dependency-properties"></a>Özel Bağımlılık Özellikleri için Etkileri  
 Özellik ayarı için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci davranışının geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması sarmalayıcıları tamamen atladığı için, özel bağımlılık özelliğiniz için sarılayıcının ayarlı tanımlarına ek bir mantık koymamalısınız. Bu tür mantığı set tanımına koyarsanız, özellik kod yerine ayarlandığında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mantık yürütülmez.  
  
 Benzer şekilde, işlemcinin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işleme özelliği [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] değerlerini elde <xref:System.Windows.DependencyObject.GetValue%2A> eden diğer yönleri de sarıcıyı kullanmak yerine kullanır. Bu nedenle, ayrıca `get` <xref:System.Windows.DependencyObject.GetValue%2A> arama ötesinde tanımda herhangi bir ek uygulama kaçınmalısınız.  
  
 Aşağıdaki örnek, özellik `public` `static` `readonly` tanımlayıcısının bir alan olarak depolandığı ve ve `get` `set` tanımların bağımlılık özelliği desteğini tanımlayan gerekli özellik sistemi yöntemlerinin ötesinde hiçbir kod içermediği sarmalayıcılarla önerilen bağımlılık özelliği tanımıdır.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Koleksiyon Türü Bağımlılık Özellikleri](collection-type-dependency-properties.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)
- [DependencyObjects için Güvenli Oluşturucu Desenleri](safe-constructor-patterns-for-dependencyobjects.md)
