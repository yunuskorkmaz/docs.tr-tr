---
title: "Nasıl yapılır: SystemParameters Kullanma"
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
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4b2ee3956017e10da8adda52fa9a0ec31cb19ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemparameters"></a>Nasıl yapılır: SystemParameters Kullanma
Bu örnek erişmek ve özelliklerini kullanmak üzere nasıl gösterir <xref:System.Windows.SystemParameters> stil veya bir düğmeyi özelleştirmek için.  
  
## <a name="example"></a>Örnek  
 Kaynaklarınızı görselleri oluşturmanıza yardımcı olması için sistem ayarları ile tutarlı olarak sistem kaynaklarını birkaç sistem tabanlı ayarları kullanıma sunar. <xref:System.Windows.SystemParameters>hem sistem parametre değeri özelliklerini hem de değerlere bağlanan kaynak anahtarları içeren bir sınıftır. Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> olan bir <xref:System.Windows.SystemParameters> özellik değeri ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> karşılık gelen kaynak anahtarı.  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyeleri kullanabilir <xref:System.Windows.SystemParameters> olarak bir statik özellik kullanımı veya dinamik kaynak başvurular (statik özellik değeri ile anahtar olarak). Uygulama çalışırken otomatik olarak güncelleştirmek için temel sistem değeri isterseniz, dinamik kaynak başvurusu kullanmak çalışır; Aksi halde, statik başvuru kullanın. Kaynak anahtarlara sahip soneki `Key` özellik adı eklenir.  
  
 Aşağıdaki örnek statik değerlerini erişmek ve nasıl kullanılacağını gösterir <xref:System.Windows.SystemParameters> stil veya bir düğmeyi özelleştirmek için. Bu biçimlendirme örneği uygulayarak bir düğme boyutları <xref:System.Windows.SystemParameters> değerleri bir düğme.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Değerleri kullanmak için <xref:System.Windows.SystemParameters> kodda, statik referans veya dinamik kaynak başvuruları kullanmak gerekmez. Bunun yerine, değerlerini kullanın <xref:System.Windows.SystemParameters> sınıfı. Anahtar olmayan özellikler görünüşe göre statik özellikler olarak, çalışma zamanı davranışını tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistem tarafından barındırılan olarak gerçek zamanlı özelliklerinde yeniden ve hesap sistem değerlerine kullanıcı tarafından yapılan değişiklikleri için düzgün biçimde değiştirilir. Aşağıdaki örnekte, genişlik ve yükseklik düğmesinin kullanarak ayarlamak gösterilmiştir <xref:System.Windows.SystemParameters> değerleri.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.SystemParameters>  
 [Sistem fırçası ile bir alanı boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemFonts kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Sistem parametreleri tuşlarını kullanma](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
