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
ms.openlocfilehash: ed608a658b5077a20ed56419c4ac731641610e3d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373081"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML Yükleme ve Bağımlılık Özellikleri
Geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasını kendi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işleyicisidir kendiliğinden bağımlılık özelliği kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] İşlemci ikili yüklerken bu özelliği sistemi yöntemleri bağımlılık özellikleri için kullanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve bağımlılık özellikleri özniteliklerini işleme. Bu özellik sarmalayıcıları etkili bir şekilde atlar. Özel bağımlılık özellikleri uyguladığınızda, bu davranışı dikkate almalı ve, özellik sarmalayıcı yöntem özelliği sistem dışında herhangi bir kod yerleştirmekten kaçınmalısınız <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda bağımlılık özellikleri hem de tüketici ve yazarı olarak anlamak ve okuduğunuz varsayılır [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md) ve [özel bağımlılık özellikleri](custom-dependency-properties.md). Ayrıca okuma [XAML genel bakış (WPF)](xaml-overview-wpf.md) ve [içinde XAML söz dizimi ayrıntı](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML yükleyici uygulaması ve performans  
 Uygulama nedenlerinden dolayı bir bağımlılık özelliği olarak bir özelliği tanımlamak ve özellik sistemi erişmek daha az yoğun <xref:System.Windows.DependencyObject.SetValue%2A> yerine özellik sarmalayıcısı ve erişilebilirliğini kullanarak ayarlamak için yöntemi. Bunun nedeni, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yedekleme kodunun yapısını biçimlendirme ve çeşitli dizeleri tarafından belirtilen tür ve üye ilişkilerine göre tüm nesne modelini Infer gerekir.  
  
 Xmlns ve derleme öznitelikleri, ancak, bir özniteliği olarak ayarlanan destekleyebilir belirleme üyeleri tanımlayan bir birleşimi yoluyla türü baktığı ve özellik değerlerini destek hangi türde kapsamlı yansıma gerektirir kullanarak <xref:System.Reflection.PropertyInfo>. Bağımlılık özellikleri verilen tür üzerinde özellik sistemi ile depolama tablo olarak erişilebilir olduğundan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasını kendi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi bu tablo kullanır ve herhangi bir algılar özelliği verilen *ABC* daha verimli bir şekilde çağrılarak ayarlanabilir <xref:System.Windows.DependencyObject.SetValue%2A> çağırılarak <xref:System.Windows.DependencyObject> türetilmiş tür, bağımlılık özelliği tanımlayıcısını kullanarak *ABC*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Özel bağımlılık özellikleri için uygulamaları  
 Çünkü geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci davranışı özellik ayarı sarmalayıcıları tamamen atlar, size herhangi ek bir mantık sarmalayıcı kümesi tanımlarını, özel bir bağımlılık özelliği için koymanız gerekir değil. Ayar tanımlarına böyle bir mantık sonra özelliği ayarlandığında mantığı yürütülmez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerine kod.  
  
 Benzer şekilde, diğer yönleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellik değerleri almak İşlemci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayrıca kullanım işleme <xref:System.Windows.DependencyObject.GetValue%2A> sarmalayıcıyı kullanmak yerine. Bu nedenle de herhangi bir ek uygulamasında kaçınmalısınız `get` tanımı ötesinde <xref:System.Windows.DependencyObject.GetValue%2A> çağırın.  
  
 Aşağıdaki örnek, önerilen bir bağımlılık özelliği olarak özellik tanımlayıcısı depolandığı sarmalayıcılar, tanımıyla bir `public` `static` `readonly` alan ve `get` ve `set` tanımlarını içeren kod yok gerekli özellik sistemi yöntemleri, yedekleme bağımlılık özelliği tanımlar.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Koleksiyon Türü Bağımlılık Özellikleri](collection-type-dependency-properties.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)
- [DependencyObjects için Güvenli Oluşturucu Desenleri](safe-constructor-patterns-for-dependencyobjects.md)
