---
title: 'Nasıl yapılır: Görselin Sapmasını Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093416"
---
# <a name="how-to-get-the-offset-of-a-visual"></a>Nasıl yapılır: Görselin Sapmasını Alma
Bu örnekler bir görsel nesnesinin veya tüm üst veya alt öğesi üst göre bir uzaklık değeri almak nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki biçimlendirme örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> ile tanımlanan <xref:System.Windows.FrameworkElement.Margin%2A> değeri 4.  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> uzaklığı alınacak yöntemi <xref:System.Windows.Controls.TextBlock>. Uzaklık değerleri içerdiği döndürülen içinde <xref:System.Windows.Vector> değeri.  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 Uzaklık dikkate <xref:System.Windows.FrameworkElement.Margin%2A> değeri. Bu durumda, <xref:System.Windows.Vector.X%2A> 4'tür ve <xref:System.Windows.Vector.Y%2A> 4'tür.  
  
 Döndürülen uzaklık değeri üst göreli olan <xref:System.Windows.Media.Visual>. Üst göreli değil bir uzaklık değeri döndürmek isterseniz bir <xref:System.Windows.Media.Visual>, kullanın <xref:System.Windows.Media.Visual.TransformToAncestor%2A> yöntemi.  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>Uzaklık bir üst aynı göreli alma  
 Aşağıdaki biçimlendirme örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> iç içe geçmiş iki içinde <xref:System.Windows.Controls.StackPanel> nesneleri.  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 Aşağıdaki çizim, biçimlendirme sonuçları gösterilmektedir.  
  
 ![Nesnelerin uzaklık değerleri](./media/visualoffset-01.png "VisualOffset_01")  
İki StackPanels'in içine TextBlock  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Windows.Media.Visual.TransformToAncestor%2A> uzaklığı alınacak yöntemi <xref:System.Windows.Controls.TextBlock> içeren göre <xref:System.Windows.Window>. Uzaklık değerleri içerdiği döndürülen içinde <xref:System.Windows.Media.GeneralTransform> değeri.  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 Uzaklık dikkate <xref:System.Windows.FrameworkElement.Margin%2A> değerleri içeren içindeki tüm nesneleri için <xref:System.Windows.Window>. Bu durumda, <xref:System.Windows.Vector.X%2A> 28 (16 + 8 +), 4 ve <xref:System.Windows.Vector.Y%2A> 28'dir.  
  
 Döndürülen uzaklık değeri üst göreli olan <xref:System.Windows.Media.Visual>. Alt öğesi için göreli bir uzaklık değeri döndürmek isterseniz bir <xref:System.Windows.Media.Visual>, kullanın <xref:System.Windows.Media.Visual.TransformToDescendant%2A> yöntemi.  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>Uzaklık bir alt öğesi için göreli alma  
 Aşağıdaki biçimlendirme örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> içinde bulunan bir <xref:System.Windows.Controls.StackPanel> nesne.  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Windows.Media.Visual.TransformToDescendant%2A> uzaklığı alınacak yöntemi <xref:System.Windows.Controls.StackPanel> göreli alt <xref:System.Windows.Controls.TextBlock>. Uzaklık değerleri içerdiği döndürülen içinde <xref:System.Windows.Media.GeneralTransform> değeri.  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 Uzaklık dikkate <xref:System.Windows.FrameworkElement.Margin%2A> tüm nesneleri için değerler. Bu durumda, <xref:System.Windows.Vector.X%2A> -4, ve <xref:System.Windows.Vector.Y%2A> -4'tür. Uzaklık değerleri negatif değerler olduğundan üst nesne olumsuz kendi alt nesneye göre uzaklığı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
