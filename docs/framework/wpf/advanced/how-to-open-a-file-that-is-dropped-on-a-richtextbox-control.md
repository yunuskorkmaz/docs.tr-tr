---
title: 'Nasıl yapılır: RichTextBox Denetimine Bırakılan bir Dosyayı Açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: f3c10ae76a9afcc04578c590cc57cd43c3ab7a1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547768"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Nasıl yapılır: RichTextBox Denetimine Bırakılan bir Dosyayı Açma
İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Documents.FlowDocument> tüm denetimleriniz yerleşik bir Sürükle ve bırak işlevi. Sürükle ve bırak metin içinde ve arasında denetimleri yerleşik işlevsellik sağlar. Ancak, dosyanın denetimindeki bırakarak bir dosyanın açılması etkinleştirmez. Bu denetimler, sürükle ve bırak olayları da işlenmiş olarak işaretleyin. Sonuç olarak, varsayılan olarak, bırakılan dosyaları açmaya işlevselliği sağlamak için kendi olay işleyicileri ekleyemezsiniz.  
  
 Bu denetimlerin sürükle ve bırak olayları için ek işleme eklemek için kullanın <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> sürükle ve bırak olayları için olay işleyicileri ekleme yöntemi. Ayarlama `handledEventsToo` parametresi `true` zaten olay yol boyunca başka bir öğe tarafından işlenmiş olarak işaretlenmiş yönlendirilmiş bir olay için çağrılan belirtilen işleyici sağlamak için.  
  
> [!TIP]
>  Yerleşik sürükle ve bırak işlevselliğini değiştirebilirsiniz <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Documents.FlowDocument> sürükle ve bırak olayları önizleme sürümleri işleme ve önizleme olayları işlenmiş olarak işaretleme. Ancak, bu yerleşik bir Sürükle ve bırak işlevi devre dışı bırakır ve önerilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek işleyicileri eklemek gösterilmiştir <xref:System.Windows.DragDrop.DragOver> ve <xref:System.Windows.DragDrop.Drop> olaylarına bir <xref:System.Windows.Controls.RichTextBox>. Bu örnekte <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> yöntemi ve kümelerini `handledEventsToo` parametresi `true` böylece olay işleyicilerini rağmen çağrılacak <xref:System.Windows.Controls.RichTextBox> bu olayları işlenmiş olarak işaretler. Olay işleyicileri kodunda üzerinde bırakılan bir metin dosyasını açmak için işlevsellik ekler <xref:System.Windows.Controls.RichTextBox>.  
  
 Bu örneği test etmek için bir metin dosyası veya zengin metin biçimi (RTF) dosyası için Windows Gezgini'nden sürükleyin <xref:System.Windows.Controls.RichTextBox>. Dosya açılacak <xref:System.Windows.Controls.RichTextBox>. Bırakma önce SHIFT tuşuna basarsanız, dosyanın dosya düz metin olarak açılacak.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
