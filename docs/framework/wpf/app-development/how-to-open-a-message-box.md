---
title: 'Nasıl yapılır: bir ileti kutusu açın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: dd79d69c9b1b54c5158b58ee2f1675e7d11a386a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545642"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="93296-102">Nasıl yapılır: bir ileti kutusu açın</span><span class="sxs-lookup"><span data-stu-id="93296-102">How to: Open a Message Box</span></span>
<span data-ttu-id="93296-103">Bu örnek bir ileti kutusu açmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="93296-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93296-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="93296-104">Example</span></span>  
 <span data-ttu-id="93296-105">Bir ileti kutusu kullanıcılara bilgilerini görüntüleme görüntülemeleri modal iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="93296-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="93296-106">Bir ileti kutusu statik çağırarak açıldığında <xref:System.Windows.MessageBox.Show%2A> yöntemi <xref:System.Windows.MessageBox> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="93296-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="93296-107">Zaman <xref:System.Windows.MessageBox.Show%2A> olduğu olarak adlandırılan, ileti bir dize parametresi kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="93296-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="93296-108">Birkaç aşırı <xref:System.Windows.MessageBox.Show%2A> bir ileti kutusu nasıl görüneceğini yapılandırmanıza izin verir (bkz: <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="93296-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="93296-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93296-109">See Also</span></span>  
 [<span data-ttu-id="93296-110">MessageBox örnek</span><span class="sxs-lookup"><span data-stu-id="93296-110">MessageBox Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160023)
