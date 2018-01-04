---
title: "Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d3acf1e5065633f9f4c75f24780230525b01ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma
Bu örnek nasıl yapılandırılacağını göstermektedir bir <xref:System.Windows.Controls.TextBox> kullanıcı girişine veya değiştirmesine izin vermeyecek şekilde denetim.  
  
## <a name="example"></a>Örnek  
 Kullanıcıların içeriği değiştirmesini önlemek için bir <xref:System.Windows.Controls.TextBox> denetlemek, Ayarla <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> özniteliğini **doğru**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Özniteliği yalnızca kullanıcı girişi etkiler; kümesinde metin etkilemez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] açıklaması bir <xref:System.Windows.Controls.TextBox> denetim veya üzerinden programlı olarak ayarlama metin <xref:System.Windows.Controls.TextBox.Text%2A> özelliği.  
  
 Varsayılan değer olan <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> olan **false**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
