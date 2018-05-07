---
title: 'Nasıl yapılır: Gönderilmiş bir Olayı İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: 80b3be439498c0dc448322d1e7daf30202a470dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-a-routed-event"></a>Nasıl yapılır: Gönderilmiş bir Olayı İşleme
Bu örnek nasıl kabarcıklanma olayları iş ve nasıl yönlendirilmiş olay verileri işlemek bir işleyici yazılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], öğeleri, bir öğenin ağaç yapısında düzenlenir. Üst öğenin alt öğelerini öğe ağacındaki tarafından başlangıçta gerçekleştirilen olayları işleme katılabilir. Olay yönlendirme nedeniyle bu mümkün olur.  
  
 Yönlendirilmiş olaylar genellikle tırmanmasını veya tünel iki yönlendirme stratejiler birini izleyin. Bu örnek kabarcıklanma olayı üzerinde odaklanır ve kullanır <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> yönlendirmenin nasıl çalıştığını göstermek için olay.  
  
 Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Controls.Button> denetler ve kullandığı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik olan bu örnekte bir ortak üst öğesi için bir olay işleyicisi iliştirmek için sözdizimini <xref:System.Windows.Controls.StackPanel>. Her biri için ayrı ayrı olay işleyicileri ekleme yerine <xref:System.Windows.Controls.Button> alt öğesi örnek öznitelik sözdizimini kullanır olay işleyicisi iliştirmek için <xref:System.Windows.Controls.StackPanel> üst öğesi. Bu olay işleme deseni bir işleyici eklendiği öğelerin sayısını azaltmak için bir yöntem olarak olay yönlendirme kullanmayı gösterir. Her tüm kabarcıklanma olayları <xref:System.Windows.Controls.Button> üst öğenin yönlendir.  
  
 Üst öğede unutmayın <xref:System.Windows.Controls.StackPanel> öğesi, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öznitelik adlandırarak kısmen yetkili olarak belirtilen olay adı <xref:System.Windows.Controls.Button> sınıfı. <xref:System.Windows.Controls.Button> Sınıfı bir <xref:System.Windows.Controls.Primitives.ButtonBase> olan sınıfın türetildiği <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay sınıftır. O anda işlenen olay üyeleri yoksa, olay işleyicisi iliştirmek için kısmi nitelik tekniği gereklidir yönlendirilmiş olay işleyicinin bağlı öğesinin listesi.  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 Aşağıdaki örnek tanıtıcıları <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  Örnek hangi öğesi olayını işler ve hangi öğesi olayını bildirir. Kullanıcı ya da düğmesini tıklattığında olay işleyicisi yürütülür.  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.RoutedEvent>  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [Ayrıntılı XAML Sözdizimi](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
