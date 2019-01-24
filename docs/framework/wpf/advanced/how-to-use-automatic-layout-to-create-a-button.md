---
title: 'Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 501341f0e71e6e5a224c51e4ae01c68ce6b845cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543493"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma
Bu örnek, bir yerelleştirilebilir uygulamasında bir düğme oluşturmak için otomatik düzen yaklaşımı kullanmayı açıklar.  
  
 Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zaman alıcı bir işlem olabilir. Yerelleştiriciler genellikle, yeniden boyutlandırabilir ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak gerekir. Geçmişteki her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gerekli ayarlamaya yönelik uyarlandığı. Artık yeteneklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeleri tasarlayabilirsiniz. Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamaları yazma yaklaşımı adlı `automatic layout`.  
  
 Aşağıdaki iki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler bir düğme; İngilizce metni ile diğeri yaratır örneği uygulamalar oluşturur. Kod metni dışında aynı olduğuna dikkat edin; Düğme metin sığdırmak için ayarlar.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Aşağıdaki grafikte, kod örnekleri çıktısını gösterir.  
  
 ![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Otomatik yeniden boyutlandırılabilir düğmesi  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Otomatik Düzen Kullanımına Genel Bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
- [Otomatik Düzen için Kılavuz Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
