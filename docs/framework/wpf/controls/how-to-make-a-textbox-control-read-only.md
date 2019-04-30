---
title: 'Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 7f24458eb98bd669d59f15c49d1d9e3beb6833b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770948"
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma
Bu örnek nasıl yapılandırılacağını gösteren bir <xref:System.Windows.Controls.TextBox> denetimi kullanıcı girişi veya değiştirilmesine izin verilmez.  
  
## <a name="example"></a>Örnek  
 Kullanıcıların içeriği değiştirmesini önlemek için bir <xref:System.Windows.Controls.TextBox> denetlemek için ayarlayın <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> özniteliğini **true**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Özniteliği yalnızca kullanıcı girişi etkiler; kümesinde metin etkilemez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] açıklaması bir <xref:System.Windows.Controls.TextBox> denetimi veya metin üzerinden programlı olarak ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliği.  
  
 Varsayılan değer olan <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> olduğu **false**.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
