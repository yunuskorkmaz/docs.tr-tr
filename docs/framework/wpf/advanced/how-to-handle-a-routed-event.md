---
title: 'Nasıl yapılır: Yönlendirilmiş Olayı İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: edb3d6724af89b7e85986c50b579084e3c4e5070
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211601"
---
# <a name="how-to-handle-a-routed-event"></a>Nasıl yapılır: Yönlendirilmiş Olayı İşleme
Bu örnek nasıl tırmanma olayları iş ve nasıl yönlendirilmiş olay verileri işleyen bir işleyici yazılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], öğeleri bir öğe ağaç yapısında düzenlenir. Üst öğe, başlangıçta öğe ağacında bir alt öğe tarafından oluşturulan olayları işleme katılabilir. Olay yönlendirme nedeniyle bu olasıdır.  
  
 Yönlendirilmiş olaylar genellikle tırmanma veya tünel iki yönlendirme stratejileri birini izleyin. Bu örnek, tırmanma olayı üzerinde odaklanır ve kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> yönlendirmenin nasıl çalıştığını göstermek için olay.  
  
 Aşağıdaki örnek iki oluşturur <xref:System.Windows.Controls.Button> denetler ve kullandığı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik olan bu örnekte bir üst öğe, bir olay işleyicisi eklemek için sözdizimi <xref:System.Windows.Controls.StackPanel>. Her biri için ayrı bir olay işleyicileri ekleme yerine <xref:System.Windows.Controls.Button> alt öğesi örnekte öznitelik sözdizimi için olay işleyicisi eklemek için <xref:System.Windows.Controls.StackPanel> üst öğe. Bu olay işleme düzen işleyicisi eklendiği öğelerin sayısını azaltmak için bir yöntem olarak olay yönlendirme kullanmayı gösterir. Tırmanma olayları her <xref:System.Windows.Controls.Button> yolunun üst öğesi.  
  
 Üst öğede unutmayın <xref:System.Windows.Controls.StackPanel> öğesi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öznitelik adlandırarak kısmen tam olarak belirtilen olay adı <xref:System.Windows.Controls.Button> sınıfı. <xref:System.Windows.Controls.Button> Sınıfı bir <xref:System.Windows.Controls.Primitives.ButtonBase> türetilmiş sınıf <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay sınıftır. Bir olay işleyicisi eklemek için bu kısmi nitelik teknik o anda işlenen olay üyeleri mevcut değilse gerekli olan yönlendirilmiş olay işleyicisi bağlı olduğu öğesinin listeleme.  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 Aşağıdaki örnek tutamaçları <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  Örnek raporları hangi öğe olayını işler ve hangi öğe olayını başlatır. Kullanıcı herhangi bir düğmeyi tıkladığında bir olay işleyicisi yürütülür.  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.RoutedEvent>
- [Girişe Genel Bakış](input-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nasıl Yapılır Konuları](events-how-to-topics.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
