---
title: "Nasıl yapılır: İçeriğin FlowDirection'ını Program Aracılığıyla Değiştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: ec159ed0efce8b5514788331e8715a55e7a8a638
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359334"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Nasıl yapılır: İçeriğin FlowDirection'ını Program Aracılığıyla Değiştirme
Bu örnek program aracılığıyla nasıl değiştirileceği gösterilmektedir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği bir <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Örnek  
 İki <xref:System.Windows.Controls.Button> öğeleri oluşturulur ve her bir olası değerlerini temsil eden <xref:System.Windows.FlowDirection>. Bir düğmeye tıklandığında, ilişkili özelliğin değeri içeriğine göre uygulanan bir <xref:System.Windows.Controls.FlowDocumentReader> adlı `tf1`.  Özellik değeri de yazılan bir <xref:System.Windows.Controls.TextBlock> adlı `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Örnek  
 Yukarıda tanımlanan düğmesine tıklama ile ilgili olaylar işlenir bir C# arka plan kod dosyası.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
