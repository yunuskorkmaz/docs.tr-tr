---
title: 'Nasıl yapılır: İleti Kutusu Açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: cf7534cdee5e17d53e95294573023d660135e395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947699"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="0239b-102">Nasıl yapılır: İleti Kutusu Açma</span><span class="sxs-lookup"><span data-stu-id="0239b-102">How to: Open a Message Box</span></span>
<span data-ttu-id="0239b-103">Bu örnek, bir ileti kutusu açma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0239b-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0239b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0239b-104">Example</span></span>  
 <span data-ttu-id="0239b-105">Bir ileti kutusu, kullanıcıların bilgilerini görüntülemek için bir görüntülemeleri kalıcı bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="0239b-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="0239b-106">Statik çağırarak bir ileti kutusu açıldığında <xref:System.Windows.MessageBox.Show%2A> yöntemi <xref:System.Windows.MessageBox> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0239b-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="0239b-107">Zaman <xref:System.Windows.MessageBox.Show%2A> olan çağrılır, iletinin dize parametresi kullanılarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0239b-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="0239b-108">İlişkin çeşitli aşırı yükler <xref:System.Windows.MessageBox.Show%2A> ileti kutusunun nasıl görüneceğini yapılandırmanıza olanak sağlar (bkz <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="0239b-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="0239b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0239b-109">See also</span></span>

- [<span data-ttu-id="0239b-110">MessageBox örnek</span><span class="sxs-lookup"><span data-stu-id="0239b-110">MessageBox Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160023)
