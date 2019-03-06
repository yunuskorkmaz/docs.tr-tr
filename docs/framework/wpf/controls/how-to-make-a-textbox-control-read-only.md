---
title: 'Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 3784471020210f995c8bb0a377d56a2466d97da1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364549"
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="cd507-102">Nasıl yapılır: TextBox Denetimini Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="cd507-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="cd507-103">Bu örnek nasıl yapılandırılacağını gösteren bir <xref:System.Windows.Controls.TextBox> denetimi kullanıcı girişi veya değiştirilmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="cd507-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd507-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd507-104">Example</span></span>  
 <span data-ttu-id="cd507-105">Kullanıcıların içeriği değiştirmesini önlemek için bir <xref:System.Windows.Controls.TextBox> denetlemek için ayarlayın <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> özniteliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="cd507-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="cd507-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Özniteliği yalnızca kullanıcı girişi etkiler; kümesinde metin etkilemez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] açıklaması bir <xref:System.Windows.Controls.TextBox> denetimi veya metin üzerinden programlı olarak ayarlama <xref:System.Windows.Controls.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cd507-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="cd507-107">Varsayılan değer olan <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> olduğu **false**.</span><span class="sxs-lookup"><span data-stu-id="cd507-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd507-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd507-108">See also</span></span>
- [<span data-ttu-id="cd507-109">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd507-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="cd507-110">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd507-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
