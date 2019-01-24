---
title: 'Nasıl yapılır: Çizgi çizmek için kalem kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: e24d02c2c6ab7537f968c013eb91838eb0bb812a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730938"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="77560-102">Nasıl yapılır: Çizgi çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="77560-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="77560-103">Çizgi çizmek için gereken bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="77560-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="77560-104"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi ve <xref:System.Drawing.Pen> nesne satır, renk ve genişlik gibi özellikleri depolar.</span><span class="sxs-lookup"><span data-stu-id="77560-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77560-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="77560-105">Example</span></span>  
 <span data-ttu-id="77560-106">Aşağıdaki örnek bir çizgi çizer (20, 10) için (300, 100).</span><span class="sxs-lookup"><span data-stu-id="77560-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="77560-107">İlk deyim kullanır <xref:System.Drawing.Pen.%23ctor%2A> siyah kalem oluşturmak için sınıf oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="77560-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="77560-108">Geçirilen bir bağımsız değişken <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu bir <xref:System.Drawing.Color> ile oluşturulan nesne <xref:System.Drawing.Color.FromArgb%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77560-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="77560-109">Oluşturmak için kullanılan değerleri <xref:System.Drawing.Color> nesne — (255, 0, 0, 0) — rengi alfa, kırmızı, yeşil ve mavi bileşenlerinin karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="77560-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="77560-110">Bu değerleri bir donuk siyah kalem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="77560-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77560-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="77560-111">Compiling the Code</span></span>  
 <span data-ttu-id="77560-112">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="77560-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77560-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77560-113">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="77560-114">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="77560-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="77560-115">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="77560-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
