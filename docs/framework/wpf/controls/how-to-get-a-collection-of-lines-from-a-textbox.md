---
title: "Nasıl yapılır: TextBox'dan Satır Koleksiyonu Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb771cdb4d12ebaa5160ec16ca57ba6acf011222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Nasıl yapılır: TextBox'dan Satır Koleksiyonu Alma
Bu örnek metinden satırları koleksiyonunu alma gösterilmektedir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alan basit bir yöntemi gösterir bir <xref:System.Windows.Controls.TextBox> döndürür ve bağımsız değişkeni olarak bir <xref:System.Collections.Specialized.StringCollection> metinde satırları içeren **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Özelliği kaç satır halen olduğunu belirlemek için kullanılan **TextBox**ve <xref:System.Windows.Controls.TextBox.GetLineText%2A> yöntemi her satırı ayıklamak ve satırları koleksiyona eklemek için sonra kullanılır.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TextBox genel bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
