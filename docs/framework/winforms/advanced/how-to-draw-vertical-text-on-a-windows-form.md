---
title: 'Nasıl yapılır: Bir Windows Formunda Dikey Metin Çizme'
ms.date: 03/30/2017
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
ms.openlocfilehash: eb00928205a318b068d49ea3f6f71c398f77bbcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61722919"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="dab2a-102">Nasıl yapılır: Bir Windows Formunda Dikey Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="dab2a-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="dab2a-103">Aşağıdaki kod örneği kullanarak bir form üzerinde dikey metin çizme gösterilmiştir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="dab2a-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dab2a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dab2a-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dab2a-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="dab2a-105">Compiling the Code</span></span>  
 <span data-ttu-id="dab2a-106">Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="dab2a-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="dab2a-107">Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="dab2a-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="dab2a-108">İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dab2a-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dab2a-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="dab2a-109">Robust Programming</span></span>  
 <span data-ttu-id="dab2a-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="dab2a-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="dab2a-111">Arial yazı tipi yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="dab2a-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab2a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dab2a-112">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="dab2a-113">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="dab2a-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="dab2a-114">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="dab2a-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
