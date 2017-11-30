---
title: "XAML Yükleme ve Bağımlılık Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97970a8a292eee43b01b1eab235376ae9b8e6fad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML Yükleme ve Bağımlılık Özellikleri
Geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uyarlamasını kendi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci olduğu kendiliğinden bağımlılık özelliği kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] İşlemci ikili yüklerken bu özelliği sistem yöntemleri bağımlılık özellikleri için kullanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve bağımlılık özellikleri öznitelikleri işleme. Bu özellik sarmalayıcıları etkili bir şekilde atlar. Özel bağımlılık özelliklerini uygularken, bu davranışı dikkate almalı ve, özellik sarmalayıcısı sistem yöntem özelliği dışındaki başka bir kod yerleştirmekten kaçınmalısınız <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliklerini hem de tüketici ve yazar olarak anladığınızı ve okuma varsayar [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) ve [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md). Ayrıca okumalısınız [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) ve [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML yükleyici uygulaması ve performans  
 Uygulama nedenlerinden dolayı bir özelliği bir bağımlılık özelliği olarak tanımlamak ve özellik sistemi erişmek pkı'ya daha ucuz <xref:System.Windows.DependencyObject.SetValue%2A> yerine özellik sarmalayıcısı ve onun ayarlayıcı kullanarak ayarlamak için yöntem. Bunun nedeni, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci biçimlendirme ve çeşitli dizeleri yapısı tarafından belirtilen tür ve üye ilişkilerine dayalı yedekleme kodunun tüm nesne modelini Infer gerekir.  
  
 Türü, xmlns ve derleme özniteliklerinin ancak, bir özniteliği olarak ayarlanan destekleyebilir belirleme üyeleri tanımlayan bir birleşimiyle aranır ve özellik değerlerini destek hangi türde çözme kapsamlı yansıma gerektirir kullanarak <xref:System.Reflection.PropertyInfo>. Belirli bir türde bağımlılık özellikleri özellik sistemi aracılığıyla depolama tablosu olarak erişilebilir olduğundan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uyarlamasını kendi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi bu tablo kullanır ve herhangi bir oluşturur özelliği verilen *ABC* daha verimli bir şekilde çağırarak ayarlanabilir <xref:System.Windows.DependencyObject.SetValue%2A> çağırılarak <xref:System.Windows.DependencyObject> türetilmiş türü, bağımlılık özelliği tanımlayıcı kullanılarak *ABC*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Özel bağımlılık özelliklerinin etkileri  
 Çünkü geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uyarlamasını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellik ayarı için işlemci davranışı sarmalayıcıları tamamen atladığından, size herhangi bir ek mantık sarmalayıcı kümesi tanımları özel bağımlılık özelliği için yerleştirileceği değil. Ayar tanımlarına böyle bir mantık sonra özelliği ayarlandığında mantığı çalıştırılmayacak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerine kodu.  
  
 Benzer şekilde, diğer yönlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellik değerleri elde İşlemci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayrıca kullanım işleme <xref:System.Windows.DependencyObject.GetValue%2A> sarmalayıcı kullanarak yerine. Bu nedenle, aynı zamanda herhangi bir ek uygulamasında kaçınmalısınız `get` ötesinde tanımı <xref:System.Windows.DependencyObject.GetValue%2A> çağırın.  
  
 Aşağıdaki örnekte bir önerilen bağımlılık özelliği olarak özellik tanımlayıcısı depolandığı sarmalayıcıları tanımıdır bir `public` `static` `readonly` alan ve `get` ve `set` tanımlarını içeren kodu yok gerekli özellik sistemi yöntemleri, yedekleme bağımlılık özelliği tanımlayın.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Koleksiyon türü bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Bağımlılık özelliği güvenlik](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [DependencyObjects için güvenli oluşturucu desenler](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
