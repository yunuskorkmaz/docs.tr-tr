---
title: 'Nasıl yapılır: Ileti kutusu açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123733"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="ec954-102">Nasıl yapılır: Ileti kutusu açma</span><span class="sxs-lookup"><span data-stu-id="ec954-102">How to: Open a Message Box</span></span>
<span data-ttu-id="ec954-103">Bu örnekte bir ileti kutusunun nasıl açılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ec954-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec954-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec954-104">Example</span></span>  
 <span data-ttu-id="ec954-105">İleti kutusu, kullanıcılara bilgi görüntülemek için önceden yazılmış bir kalıcı iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="ec954-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="ec954-106"><xref:System.Windows.MessageBox> sınıfının statik <xref:System.Windows.MessageBox.Show%2A> yöntemi çağırarak bir ileti kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="ec954-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="ec954-107"><xref:System.Windows.MessageBox.Show%2A> çağrıldığında, ileti dize parametresi kullanılarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ec954-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="ec954-108"><xref:System.Windows.MessageBox.Show%2A> birkaç aşırı yüklemesi, bir ileti kutusunun nasıl görüneceğini yapılandırmanıza olanak tanır (bkz. <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="ec954-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="ec954-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec954-109">See also</span></span>

- [<span data-ttu-id="ec954-110">MessageBox örneği</span><span class="sxs-lookup"><span data-stu-id="ec954-110">MessageBox Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
