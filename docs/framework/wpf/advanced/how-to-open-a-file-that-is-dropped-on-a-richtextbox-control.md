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
ms.openlocfilehash: 408d48856362fa8a77a44e2cc97cb2d5ff608dcf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046347"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Nasıl yapılır: RichTextBox Denetimine Bırakılan bir Dosyayı Açma

İçinde,, ve<xref:System.Windows.Documents.FlowDocument> denetimlerinin hepsi yerleşik sürükle ve bırak işlevselliğine sahiptir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> Yerleşik işlevsellik, denetimin içindeki ve içindeki metnin sürükleme ve bırakma işlevlerini sunar. Ancak, dosyayı denetimde bırakarak bir dosyayı açmayı etkinleştirmez. Bu denetimler Ayrıca sürükle ve bırak olaylarını işlenmiş olarak işaretler. Sonuç olarak, bırakılan dosyaları açan işlevselliği sağlamak için varsayılan olarak kendi olay işleyicilerinizi ekleyemezsiniz.

Bu denetimlerde sürükle ve bırak olaylarına ek işleme eklemek için, sürükle ve bırak olayları için olay <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> işleyicilerinizi eklemek üzere yöntemini kullanın. Parametresi, daha önce `true` olay rotası boyunca başka bir öğe tarafından işlenmiş olarak işaretlenmiş bir yönlendirilmiş olay için belirtilen işleyicinin çağrılması için olarak ayarlayın. `handledEventsToo`

> [!TIP]
> Sürükle ve bırak olaylarının önizleme sürümlerini işleyerek ve önizleme olaylarını işlenmiş olarak işaretleyerek, <xref:System.Windows.Controls.TextBox>ve <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Documents.FlowDocument> ' nin yerleşik sürükle ve bırak işlevini değiştirebilirsiniz. Bununla birlikte, bu, yerleşik sürükle ve bırak işlevlerini devre dışı bırakır ve önerilmez.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Windows.DragDrop.DragOver> içindeki ve <xref:System.Windows.DragDrop.Drop> olayları <xref:System.Windows.Controls.RichTextBox>için işleyicilerin nasıl ekleneceğini gösterir. Bu <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> örnek, yöntemini kullanır ve bu olayları `handledEventsToo` işlenmiş olarak `true` <xref:System.Windows.Controls.RichTextBox> işaretlese de olayları işleyicileri çağrılacak şekilde parametresini olarak ayarlar. Olay işleyicilerindeki kod, <xref:System.Windows.Controls.RichTextBox>üzerinde bırakılan bir metin dosyasını açmak için işlevsellik ekler.

Bu örneği test etmek için bir metin dosyası veya bir zengin metin biçimi (RTF) dosyasını Windows Gezgini 'nden öğesine <xref:System.Windows.Controls.RichTextBox>sürükleyin. Dosya içinde <xref:System.Windows.Controls.RichTextBox>açılır. Dosyayı bırakmadan önce SHIFT tuşuna basarsanız dosya düz metin olarak açılır.

[!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]

[!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
[!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
