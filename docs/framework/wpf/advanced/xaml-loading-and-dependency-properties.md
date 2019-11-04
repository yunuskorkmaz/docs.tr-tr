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
ms.openlocfilehash: 57c25297f995acd1ef307466258b5f4e03cc3098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459539"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML Yükleme ve Bağımlılık Özellikleri
[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanması, kendiliğinden bağımlılık özelliği farkındır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi, ikili [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yüklenirken ve bağımlılık özellikleri olan öznitelikleri işlerken bağımlılık özellikleri için özellik sistemi yöntemlerini kullanır. Bu özellik sarmalayıcıları etkin bir şekilde atlar. Özel bağımlılık özellikleri uyguladığınızda, bu davranışı dikkate almalısınız ve özellik sarmalayıcısında başka bir kodu, <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A>özellik dışında bir şekilde yerleştirmekten kaçınmalısınız.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konu, bağımlılık özelliklerini hem tüketici hem de yazar olarak anladığınızı ve okuma [bağımlılığı özelliklerine genel bakış](dependency-properties-overview.md) ve [Özel bağımlılık özellikleri](custom-dependency-properties.md)kullandığınızı varsayar. Ayrıca ayrıntılı [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) ve [xaml söz dizimi](xaml-syntax-in-detail.md)da vardır.  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML yükleyici uygulama ve performans  
 Uygulama nedenleriyle, bağımlılık özelliği olarak bir özelliği belirlemek ve özellik sarmalayıcı ve ayarlayıcısı kullanmak yerine, özellik sistemine <xref:System.Windows.DependencyObject.SetValue%2A> metoduna erişmek için hesaplama daha ucuzdur. Bunun nedeni, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin, yalnızca biçimlendirme yapısına ve çeşitli dizelere göre belirtilen tür ve üye ilişkilerini bilmenin yanı sıra, yedekleme kodunun tüm nesne modelini temel almalıdır.  
  
 Tür, xmlns ve derleme özniteliklerinin bir birleşimi ile aranır, ancak üyelerini tanımlar, hangisinin öznitelik olarak ayarlanmakta olduğunu belirler ve özellik değerlerinin desteklediği türleri çözümlemek için kapsamlı yansıma gerekir <xref:System.Reflection.PropertyInfo>kullanma. Verilen bir türdeki bağımlılık özellikleri, özellik sistemi aracılığıyla bir depolama tablosu olarak erişilebilir olduğundan, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanması bu tabloyu kullanır ve *ABC* 'nin verilen tüm özelliği tarafından daha verimli bir şekilde ayarlanabilir. bağımlılık özelliği tanımlayıcı *abcözelliğini*kullanarak kapsayan <xref:System.Windows.DependencyObject> türetilmiş tür üzerinde <xref:System.Windows.DependencyObject.SetValue%2A> çağrılıyor.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Özel bağımlılık özelliklerinin etkileri  
 Özellik ayarı için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci davranışının geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanması, sarmalayıcıları tamamen atladığından, Özel bağımlılık özelliği için sarmalayıcının küme tanımlarına ek bir mantık koymamalısınız. Bu tür mantığı küme tanımına yerleştirirseniz, özellik kod yerine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayarlandığında Logic yürütülmez.  
  
 Benzer şekilde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemeden özellik değerlerini elde eden [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin diğer yönleri de sarmalayıcı kullanmak yerine <xref:System.Windows.DependencyObject.GetValue%2A> kullanır. Bu nedenle, <xref:System.Windows.DependencyObject.GetValue%2A> çağrısının ötesinde `get` tanımında ek herhangi bir uygulamayı da kullanmaktan kaçının.  
  
 Aşağıdaki örnek, özellik tanımlayıcısının bir `public` `static` `readonly` alanı olarak depolandığı ve `get` ve `set` tanımlarının gerekli özelliğin ötesinde hiçbir kod içermediği sarmalayıcılarla önerilen bir bağımlılık özelliği tanımıdır. bağımlılık özelliği yedeklemesini tanımlayan sistem yöntemleri.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Koleksiyon Türü Bağımlılık Özellikleri](collection-type-dependency-properties.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)
- [DependencyObjects için Güvenli Oluşturucu Desenleri](safe-constructor-patterns-for-dependencyobjects.md)
