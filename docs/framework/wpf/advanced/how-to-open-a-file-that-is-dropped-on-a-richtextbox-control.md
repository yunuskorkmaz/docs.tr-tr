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
ms.openlocfilehash: 8ffa4c9919788060dc4524e127c181ee8282e6f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768608"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Nasıl yapılır: RichTextBox Denetimine Bırakılan bir Dosyayı Açma
İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Documents.FlowDocument> denetimlerinin tüm yerleşik bir Sürükle ve bırak işlevi vardır. Sürükle ve bırak metin içindeki ve arasındaki denetimleri yerleşik işlevsellik sağlar. Ancak, dosyanın denetimi bırakarak bir dosyayı açmayı etkinleştirmez. Bu denetimler ayrıca sürükle ve bırak olayları işlenmiş olarak işaretleyin. Sonuç olarak, varsayılan olarak, bırakılan dosyaları açmak için işlevselliği sağlamak için kendi olay işleyicileri ekleyemezsiniz.  
  
 Sürükle ve bırak olayları için ek işleme bu denetimleri eklemek için <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> , sürükle ve bırak olayları için olay işleyicileri ekleme yöntemi. Ayarlama `handledEventsToo` parametresi `true` belirtilen işleyici zaten olay yol boyunca başka bir öğe tarafından işlenmiş olarak işaretlenmiş gönderilmiş bir olay için çağrılması için.  
  
> [!TIP]
>  Yerleşik sürükle ve bırak işlevlerini değiştirebilirsiniz <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Documents.FlowDocument> sürükle ve bırak olayları önizleme sürümleri işleme ve önizleme olayları işlenmiş olarak işaretleme. Ancak, bu yerleşik sürükle ve bırak işlevlerini devre dışı bırakır ve önerilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, işleyicileri eklemek gösterilmiştir <xref:System.Windows.DragDrop.DragOver> ve <xref:System.Windows.DragDrop.Drop> olaylarına bir <xref:System.Windows.Controls.RichTextBox>. Bu örnekte <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> yöntemi ve kümelerini `handledEventsToo` parametresi `true` böylece olay işleyicileri olsa bile çağrılacak <xref:System.Windows.Controls.RichTextBox> bu olayları işlenmiş olarak işaretler. Olay işleyicilerine kod üzerinde bırakılan bir metin dosyası açmak için işlevsellik ekler <xref:System.Windows.Controls.RichTextBox>.  
  
 Bu örnekte test etmek için bir metin veya zengin metin biçimi (RTF) dosyası için Windows Gezgini'nden sürükleyin <xref:System.Windows.Controls.RichTextBox>. Dosya içinde açılır <xref:System.Windows.Controls.RichTextBox>. Bırakma önce SHIFT tuşuna basarsanız, dosya dosya düz metin olarak açılacak.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
