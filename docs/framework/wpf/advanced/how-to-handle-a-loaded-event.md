---
title: 'Nasıl yapılır: Yüklü Bir Olayı İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: a4916d3cfd20d082a8466f61fc74e16db2f0f346
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353354"
---
# <a name="how-to-handle-a-loaded-event"></a>Nasıl yapılır: Yüklü Bir Olayı İşleme
Bu örnek nasıl işleneceğini gösterir <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> olay ve olay işleme için uygun bir senaryo. İşleyici oluşturur bir <xref:System.Windows.Controls.Button> Sayfa yüklediğinde.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] birlikte bir arka plan kod dosyası.  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.FrameworkElement>
- [Nesne Yaşam Süresi Olayları](object-lifetime-events.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nasıl Yapılır Konuları](base-elements-how-to-topics.md)
