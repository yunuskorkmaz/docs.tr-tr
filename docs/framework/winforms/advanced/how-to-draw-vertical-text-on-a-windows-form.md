---
title: "Nasıl yapılır: Bir Windows Formunda Dikey Metin Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76da7be50f9e12454e16e08ec4db494585fae613
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="69fe7-102">Nasıl yapılır: Bir Windows Formunda Dikey Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="69fe7-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="69fe7-103">Aşağıdaki kod örneği kullanarak bir formunda dikey metin çizme gösterilmektedir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="69fe7-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69fe7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="69fe7-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69fe7-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="69fe7-105">Compiling the Code</span></span>  
 <span data-ttu-id="69fe7-106">Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="69fe7-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="69fe7-107">Formu yeniden boyutlandırılmış veya başka bir form tarafından getirilmemeli çizilmiş içeriği yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="69fe7-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="69fe7-108">İçeriğinizi otomatik olarak yeniden boyamak yapmak için geçersiz kılmalıdır <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="69fe7-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="69fe7-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="69fe7-109">Robust Programming</span></span>  
 <span data-ttu-id="69fe7-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="69fe7-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="69fe7-111">Arial yazı tipi yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="69fe7-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69fe7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69fe7-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="69fe7-113">Grafik programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="69fe7-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="69fe7-114">Yazı tipleri ve metin kullanma</span><span class="sxs-lookup"><span data-stu-id="69fe7-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
