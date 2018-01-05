---
title: "Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbd8bd7e36b7b773837b839e77ec88a8e7c8f0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma
Bu örnek, otomatik düzen yaklaşımı yerelleştirilebilir bir uygulama oluşturmak için bir kılavuz kullanmayı açıklar.  
  
 Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uzun süren bir işlem olabilir. Yeniden Boyutlandır ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak genellikle çevirmenlerin gerekir. Geçmişte her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için gerekli ayarlama uyarlandığı. Şimdi özelliklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeler tasarlayabilirsiniz. Daha kolay yeniden boyutlandırılmış ve konumlandırılabilir uygulamaları yazma yaklaşımına adlı `auto layout`.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, bazı düğmeler ve metin konumlandırmak için kılavuz kullanmayı gösterir. Hücrelerin genişliği ve yüksekliği ayarlanır bildirimi `Auto`; bu nedenle bir görüntüyle düğmeyi içeren hücre Resmi sığacak şekilde ayarlanır. Çünkü <xref:System.Windows.Controls.Grid> öğesi içeriğini yararlı olabilir yerelleştirilebilir uygulamalar tasarlamada için otomatik düzen yaklaşımını almak için ayarlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir kılavuz kullanmayı gösterir.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Aşağıdaki grafikte kod örneği çıktısını gösterir.  
  
 ![Kılavuz örnek](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Kılavuz  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomatik Düzen Kullanımına Genel Bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Düğme Oluşturmak için Otomatik Düzeni Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
