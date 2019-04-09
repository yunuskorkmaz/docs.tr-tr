---
title: 'Nasıl yapılır: ScrollViewer ile bir Genişletici Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: ef0bc5d344f7d465de9209708430d3e61d40d4f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114656"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>Nasıl yapılır: ScrollViewer ile bir Genişletici Oluşturma
Bu örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Expander> içeren bir görüntü ve metin gibi karmaşık içerik denetimi. Bu örnek ayrıca içeriğini barındırır <xref:System.Windows.Controls.Expander> içinde bir <xref:System.Windows.Controls.ScrollViewer> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Expander>. Örnekte bir <xref:System.Windows.Controls.Primitives.BulletDecorator> tanımlamak için bir görüntü ve metin içeren bir denetim <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>. A <xref:System.Windows.Controls.ScrollViewer> denetim genişletilmiş içerik kaydırma bir yöntem sunar.  
  
 Örnek ayarlar Not <xref:System.Windows.FrameworkElement.Height%2A> özelliği <xref:System.Windows.Controls.ScrollViewer> yerine içerik üzerinde. Varsa <xref:System.Windows.FrameworkElement.Height%2A> içeriğe göre ayarlanır <xref:System.Windows.Controls.ScrollViewer> içerik kaydırma kullanıcıya izin vermiyor. <xref:System.Windows.FrameworkElement.Width%2A> Özelliği ayarlanmış <xref:System.Windows.Controls.Expander> denetimi ve bu ayar uygulandığı <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve genişletilmiş içeriği.  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Expander>
- [Genişleticiye Genel Bakış](expander-overview.md)
- [Nasıl Yapılır Konuları](expander-how-to-topics.md)
