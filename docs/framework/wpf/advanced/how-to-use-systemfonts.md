---
title: "Nasıl yapılır: SystemFonts Kullanma"
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
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ce82724a4e9a547b8441628f43621f29eab6307
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemfonts"></a>Nasıl yapılır: SystemFonts Kullanma
Bu örnek, statik kaynaklarının nasıl kullanılacağını gösterir <xref:System.Windows.SystemFonts> stil ya da bir düğmeyi özelleştirmek amacıyla sınıfı.  
  
## <a name="example"></a>Örnek  
 Sistem kaynakları sistem ayarları ile tutarlı görselleri oluşturmanıza yardımcı olması için birkaç sistem tarafından belirlenen değerleri hem kaynak hem de özellikleri olarak kullanıma sunar. <xref:System.Windows.SystemFonts>statik özellikler ve bu değerleri çalışma zamanında dinamik olarak erişmek için kullanılan kaynak anahtarlara başvuran özellikleri olarak her iki sistem yazı tipi değerlerini içeren bir sınıftır. Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> olan bir <xref:System.Windows.SystemFonts> değeri ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> karşılık gelen bir kaynak anahtardır.  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyeleri kullanabilir <xref:System.Windows.SystemFonts> olarak statik özellik veya dinamik kaynak başvurular (statik özellik değeri ile anahtar olarak). Uygulama çalışırken otomatik olarak güncelleştirmek için yazı tipi ölçüsünün isterseniz, dinamik kaynak başvurusu kullanmak çalışır; Aksi takdirde statik referans kullanın.  
  
> [!NOTE]
>  Kaynak anahtarlarının eklenen özellik adı "Tuş" son ekine sahip.  
  
 Aşağıdaki örnek erişmek ve özelliklerini kullanmak üzere nasıl gösterir <xref:System.Windows.SystemFonts> stil veya bir düğmeyi özelleştirmek için statik değerler olarak. Bu biçimlendirme örneği atar <xref:System.Windows.SystemFonts> değerleri bir düğme.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Değerleri kullanmak için <xref:System.Windows.SystemFonts> kod içinde statik bir değer veya dinamik kaynak başvurusu kullanmanız gerekmez. Bunun yerine, anahtar olmayan özelliklerini kullanın <xref:System.Windows.SystemFonts> sınıfı. Anahtar olmayan özellikler görünüşe göre statik özellikler olarak, çalışma zamanı davranışını tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarafından barındırılan olarak sistem gerçek zamanlı özelliklerinde yeniden ve düzgün şekilde sistem değerlerine kullanıcı tarafından yapılan değişiklikleri hesaba katmayacak. Aşağıdaki örnek, bir düğme yazı tipi ayarlarını belirtmek gösterilmiştir.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.SystemFonts>  
 [Sistem fırçası ile bir alanı boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemParameters kullanımı](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Sistem yazı tiplerini tuşlarını kullanın](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [x: Static işaretleme uzantısı](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [DynamicResource Biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
