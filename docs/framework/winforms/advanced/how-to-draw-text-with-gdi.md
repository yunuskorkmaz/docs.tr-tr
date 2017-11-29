---
title: "Nasıl yapılır: GDI ile Metin Çizme"
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
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48644ce8449c8d8eea7306eff1e43539659370c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="67ced-102">Nasıl yapılır: GDI ile Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="67ced-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="67ced-103">İle <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yönteminde <xref:System.Windows.Forms.TextRenderer> sınıfı, erişebilir [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bir form veya denetim metin çizme işlevi.</span><span class="sxs-lookup"><span data-stu-id="67ced-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]<span data-ttu-id="67ced-104">metin işleme genellikle daha iyi performans ve daha ölçmek daha doğru metin sunar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67ced-104"> text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67ced-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemlerinin <xref:System.Windows.Forms.TextRenderer> sınıfı yazdırmak için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="67ced-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="67ced-106">Yazdırma sırasında her zaman kullanmak <xref:System.Drawing.Graphics.DrawString%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="67ced-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67ced-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="67ced-107">Example</span></span>  
 <span data-ttu-id="67ced-108">Aşağıdaki kod örneği kullanarak bir dikdörtgen içinde birden çok satıra metin çizme gösterilmiştir <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67ced-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="67ced-109">Metinle işlemek için <xref:System.Windows.Forms.TextRenderer> ihtiyacınız sınıfı, bir <xref:System.Drawing.IDeviceContext>, gibi bir <xref:System.Drawing.Graphics> ve <xref:System.Drawing.Font>, metin ve, bunu çizilip rengi çizmek için bir konum.</span><span class="sxs-lookup"><span data-stu-id="67ced-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="67ced-110">İsteğe bağlı olarak, metin kullanarak biçimlendirme belirtebilirsiniz <xref:System.Windows.Forms.TextFormatFlags> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="67ced-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="67ced-111">Edinme hakkında daha fazla bilgi için bir <xref:System.Drawing.Graphics>, bkz: [nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="67ced-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="67ced-112">Oluşturma hakkında daha fazla bilgi için bir <xref:System.Drawing.Font>, bkz: [nasıl yapılır: yazı tipi aileleri oluşturmak ve yazı tipleri](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="67ced-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="67ced-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="67ced-113">Compiling the Code</span></span>  
 <span data-ttu-id="67ced-114">Önceki kod örneğinde Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="67ced-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ced-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67ced-115">See Also</span></span>  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [<span data-ttu-id="67ced-116">Yazı tipleri ve metin kullanma</span><span class="sxs-lookup"><span data-stu-id="67ced-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
