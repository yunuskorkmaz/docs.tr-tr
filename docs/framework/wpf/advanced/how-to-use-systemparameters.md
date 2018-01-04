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
ms.workload: dotnet
ms.openlocfilehash: ec333fbc30374ff6f8e2e7674ab332644ff7aad0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [Sistem Fırçası ile bir Alanı Boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemFonts Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Sistem Parametreleri Tuşlarını Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
