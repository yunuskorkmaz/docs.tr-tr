---
title: 'Nasıl yapılır: Metin Süslemesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185931"
---
# <a name="how-to-create-a-text-decoration"></a>Nasıl yapılır: Metin Süslemesi Oluşturma
<xref:System.Windows.TextDecoration> Nesne, metne ekleyebileceğiniz görsel bir süslemedir. Dört tür metin süslemesi vardır: altı çizili, temel, vurucu ve üst çizgi. Aşağıdaki örnek, metin süslemelerinin metne göre konumlarını gösterir.  
  
 ![Metin süsleme türleri diyagramı](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 Metne metin süslemesi eklemek <xref:System.Windows.TextDecoration> için bir nesne oluşturun ve özelliklerini değiştirin. Metin <xref:System.Windows.TextDecoration.Location%2A> süslemesinin altı çizili gibi nerede göründüğünü belirtmek için özelliği kullanın. Metin <xref:System.Windows.TextDecoration.Pen%2A> süslemesinin görünümünü belirtmek için katı dolgu veya degrade renk gibi özelliği kullanın. <xref:System.Windows.TextDecoration.Pen%2A> Özellik için bir değer belirtmezseniz, süslemeler varsayılan olarak metinle aynı renge ayrılır. Bir <xref:System.Windows.TextDecoration> nesneyi tanımladıktan sonra, <xref:System.Windows.TextDecorations> nesneyi istenen metin nesnesinin koleksiyonuna ekleyin.  
  
 Aşağıdaki örnek, doğrusal degrade fırçası ve kesikli kalemle stile sahip bir metin süslemesini gösterir.  
  
 ![Doğrusal degrade altı çizili metin süslemesi](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 Nesne, <xref:System.Windows.Documents.Hyperlink> akış içeriği içinde köprüler barındırmanızı sağlayan bir satır içi düzey akış içeriği öğesidir. Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.TextDecoration> bir alt çizgi yi görüntülemek için bir nesne kullanır. <xref:System.Windows.TextDecoration>nesneler, özellikle çok sayıda <xref:System.Windows.Documents.Hyperlink> nesne varsa, anlık olarak performans yoğun olabilir. <xref:System.Windows.Documents.Hyperlink> Öğeleri kapsamlı bir şekilde kullanırsanız, yalnızca olay gibi bir olayı tetiklerken <xref:System.Windows.ContentElement.MouseEnter> altı çiziyi göstermeyi düşünebilirsiniz.  
  
 Aşağıdaki örnekte, "MSN' mevzum" bağlantısının alt çizgi <xref:System.Windows.ContentElement.MouseEnter> altı dinamiktir ve yalnızca olay tetiklendiğinde görünür.  
  
 ![TextDecorations görüntüleyen köprüler](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 Daha fazla bilgi için [bkz.](how-to-specify-whether-a-hyperlink-is-underlined.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, altı çizili metin süslemesi varsayılan yazı tipi değerini kullanır.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 Aşağıdaki kod örneğinde, kalem için düz renkli bir fırça ile altı çizili metin süslemesi oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 Aşağıdaki kod örneğinde, kesikli kalem için doğrusal degrade fırçası ile altı çizili metin süslemesi oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Köprünün Altı Çizili Olup Olmadığını Belirtme](how-to-specify-whether-a-hyperlink-is-underlined.md)
