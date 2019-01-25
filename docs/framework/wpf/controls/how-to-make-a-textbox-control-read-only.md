---
title: 'Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 1e9d333f22099d9593e58b4087f185b2988215ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517181"
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma
Bu örnek nasıl yapılandırılacağını gösteren bir <xref:System.Windows.Controls.TextBox> denetimi kullanıcı girişi veya değiştirilmesine izin verilmez.  
  
## <a name="example"></a>Örnek  
 Kullanıcıların içeriği değiştirmesini önlemek için bir <xref:System.Windows.Controls.TextBox> denetlemek için ayarlayın <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> özniteliğini **true**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Özniteliği yalnızca kullanıcı girişi etkiler; kümesinde metin etkilemez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] açıklaması bir <xref:System.Windows.Controls.TextBox> denetimi veya metin üzerinden programlı olarak ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliği.  
  
 Varsayılan değer olan <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> olduğu **false**.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
