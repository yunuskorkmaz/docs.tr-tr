---
title: 'Nasıl yapılır: Özel Kesikli Çizgi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: d2184a8d7d7f24b8f631818608ab4bcdb89857c7
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506042"
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="72ed5-102">Nasıl yapılır: Özel Kesikli Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="72ed5-102">How to: Draw a Custom Dashed Line</span></span>
<span data-ttu-id="72ed5-103">GDI +'da listelenen birkaç çizgi stilleri sağlar <xref:System.Drawing.Drawing2D.DashStyle> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="72ed5-103">GDI+ provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="72ed5-104">Bu standart çizgi stilleri gereksinimlerinizi karşılamıyorsa, özel çizgi desenine oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72ed5-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72ed5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="72ed5-105">Example</span></span>  
 <span data-ttu-id="72ed5-106">Özel kesikli çizgi çizmek için bir dizi içinde uzunluklarını çizgi ve boşluk yerleştirin ve dizi değeri olarak atama <xref:System.Drawing.Pen.DashPattern%2A> özelliği bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="72ed5-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="72ed5-107">Aşağıdaki örnek dizisine göre özel kesikli çizgi çizer `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="72ed5-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="72ed5-108">Kalem genişliği 5 tarafından dizinin öğeleri çarpmak varsa `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="72ed5-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="72ed5-109">25 ve 75 arasındaki uzunluğu görüntülenen tireler alternatif ve alanları, uzunluğu 10 ile 20 arasında alternatif.</span><span class="sxs-lookup"><span data-stu-id="72ed5-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="72ed5-110">Aşağıdaki çizimde, sonuçta elde edilen kesikli çizgiye gösterir.</span><span class="sxs-lookup"><span data-stu-id="72ed5-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="72ed5-111">Böylece satırın son 25 birim miktarından daha kısa olacak şekilde son dash sahip unutmayın (405, 5).</span><span class="sxs-lookup"><span data-stu-id="72ed5-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="72ed5-112">![Çizim kesikli çizgiye gösterir. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="72ed5-112">![Illustration that shows a dashed line.](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72ed5-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="72ed5-113">Compiling the Code</span></span>  
 <span data-ttu-id="72ed5-114">Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="72ed5-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="72ed5-115">Önceki kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="72ed5-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ed5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72ed5-116">See also</span></span>

- [<span data-ttu-id="72ed5-117">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="72ed5-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
