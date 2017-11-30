---
title: "Nasıl yapılır: RichTextBox'dan Metin İçeriği Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f24b71bcb5f013c4b7054dd0948e5f2709230a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>Nasıl yapılır: RichTextBox'dan Metin İçeriği Ayıklama
Bu örnek, içeriği ayıklamak gösterilmiştir bir <xref:System.Windows.Controls.RichTextBox> düz metin olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu tanımlayan bir adlandırılmış <xref:System.Windows.Controls.RichTextBox> denetim basit içeriğe sahip.  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu alan bir yöntem uygulayan bir <xref:System.Windows.Controls.RichTextBox> bir bağımsız değişken olarak ve düz metin içeriğini temsil eden bir dize döndürür <xref:System.Windows.Controls.RichTextBox>.  
  
 Yöntem yeni bir oluşturur <xref:System.Windows.Documents.TextRange> içeriğinden <xref:System.Windows.Controls.RichTextBox>kullanarak <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> ve <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> ayıklanacak içeriğin aralığını belirtmek için.  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A>ve <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> özellikler her bir <xref:System.Windows.Documents.TextPointer>ve içeriğini temsil eden arka plandaki FlowDocument üzerinde erişilebilir <xref:System.Windows.Controls.RichTextBox>.  <xref:System.Windows.Documents.TextRange>düz metin bölümlerini döndüren bir metin özelliğini sağlar <xref:System.Windows.Documents.TextRange> dize olarak.  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox genel bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
