---
title: 'Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 5fa023002ac66a65e3c179434841c975287d170c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357488"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma
Bu örnek, bir kılavuz yerelleştirilebilir bir uygulama oluşturmak için otomatik düzeni yaklaşımda kullanmayı açıklar.  
  
 Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zaman alıcı bir işlem olabilir. Yerelleştiriciler genellikle, yeniden boyutlandırabilir ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak gerekir. Geçmişteki her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gerekli ayarlamaya yönelik uyarlandığı. Artık yeteneklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeleri tasarlayabilirsiniz. Daha kolay yeniden boyutlandırılmış ve konumlandırılabilir uygulamaları yazma yaklaşımı adlı `auto layout`.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, bazı düğme ve metin konumlandırmak için bir kılavuz kullanmayı gösterir. Hücre genişliği ve yüksekliği ayarlandığından bildirimi `Auto`; bu nedenle resim sığacak şekilde düğmesi bir görüntü içeren hücreye ayarlar. Çünkü <xref:System.Windows.Controls.Grid> öğesi yararlı olabilir yerelleştirilebilen uygulamalar tasarlama için otomatik düzeni yaklaşımı, içeriği ayarlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir kılavuz kullanma işlemini gösterir.  
  
 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Aşağıdaki kod örneği çıktısını gösterir.  
  
 ![Grid örneği](./media/glob-grid.png "glob_grid")  
Kılavuz  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Otomatik Düzen Kullanımına Genel Bakış](use-automatic-layout-overview.md)
- [Düğme Oluşturmak için Otomatik Düzeni Kullanma](how-to-use-automatic-layout-to-create-a-button.md)
