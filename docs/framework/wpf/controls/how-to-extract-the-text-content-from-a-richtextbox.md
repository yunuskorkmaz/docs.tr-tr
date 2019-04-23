---
title: "Nasıl yapılır: RichTextBox'dan Metin İçeriği Ayıklama"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
ms.openlocfilehash: 220da59ec893528c99014e9ec95fb185c461b291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086123"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>Nasıl yapılır: RichTextBox'dan Metin İçeriği Ayıklama
Bu örnek içeriğini ayıklamak nasıl gösterir bir <xref:System.Windows.Controls.RichTextBox> düz metin olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu tanımlayan bir adlandırılmış <xref:System.Windows.Controls.RichTextBox> denetim basit içeriğe sahip.  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod gereken yöntemini uygulayan bir <xref:System.Windows.Controls.RichTextBox> bir bağımsız değişken olarak ve düz metin içeriğini temsil eden bir dize döndürür <xref:System.Windows.Controls.RichTextBox>.  
  
 Yeni bir yöntem oluşturur <xref:System.Windows.Documents.TextRange> içeriğinden <xref:System.Windows.Controls.RichTextBox>kullanarak <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> ve <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> ayıklamak için içeriği aralığını belirtmek için.  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> ve <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> dönüş özellikleri her bir <xref:System.Windows.Documents.TextPointer>, içeriğini temsil eden temel alınan FlowDocument üzerinde erişilebilir <xref:System.Windows.Controls.RichTextBox>.  <xref:System.Windows.Documents.TextRange> düz metin bölümlerini döndüren bir metin özelliği sağlar <xref:System.Windows.Documents.TextRange> dize olarak.  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RichTextBox Genel Bakış](richtextbox-overview.md)
- [TextBox Genel Bakış](textbox-overview.md)
