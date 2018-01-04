---
title: "Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b2a7352540456b459428dd87f6c60be0b8bc08b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-system-parameters-keys"></a>Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma
Sistem kaynakları, geliştiriciler Sistem ayarları ile tutarlı görselleri oluşturmanıza yardımcı olacak kaynaklar olarak sistem ölçümleri sayısını kullanıma sunar. <xref:System.Windows.SystemParameters>sistem parametre değerlerini ve değerlere bağlanan kaynak anahtarları içeren bir sınıf — Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Sistem parametre ölçüleri statik veya dinamik kaynaklar olarak kullanılabilir. Uygulama çalışırken otomatik olarak güncelleştirmek için parametre ölçüsünün istiyorsanız, dinamik kaynak kullanın çalışır; Aksi halde statik kaynak kullanın.  
  
> [!NOTE]
>  Dinamik kaynaklarınız anahtar sözcüğü *anahtar* özellik adı eklenir.  
  
 Aşağıdaki örnek, erişim ve stil veya bir düğmeyi özelleştirmek için sistem parametre dinamik kaynaklarının nasıl kullanılacağını gösterir. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek atayarak düğmeyi boyutlandırır <xref:System.Windows.SystemParameters> düğmenin genişlik ve yükseklik değerleri.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sistem Fırçası ile bir Alanı Boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemFonts Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [SystemParameters Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
