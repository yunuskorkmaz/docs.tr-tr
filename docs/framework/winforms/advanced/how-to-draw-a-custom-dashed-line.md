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
ms.openlocfilehash: 39dde3bb45165783171326b79e98744807350952
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521621"
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="777f2-102">Nasıl yapılır: Özel Kesikli Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="777f2-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="777f2-103"> listelenen birkaç çizgi stili sağlar <xref:System.Drawing.Drawing2D.DashStyle> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="777f2-103"> provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="777f2-104">Bu standart çizgi stillerini gereksinimlerinize göre değil, özel tire deseni oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="777f2-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="777f2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="777f2-105">Example</span></span>  
 <span data-ttu-id="777f2-106">Özel kesikli çizgi çizmek için bir dizi çizgi ve boşluk uzunlukları koy ve dizi değeri olarak atamak <xref:System.Drawing.Pen.DashPattern%2A> özelliği bir <xref:System.Drawing.Pen> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="777f2-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="777f2-107">Aşağıdaki örnek dizisine göre özel kesikli çizgi çizer `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="777f2-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="777f2-108">Dizideki öğeler 5 kalem genişliği tarafından Çarp olursa, `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="777f2-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="777f2-109">25 ve 75 arasındaki uzunluğu görüntülenen tireler alternatif ve uzunluğu 10 ile 20 arasında boşluk alternatif.</span><span class="sxs-lookup"><span data-stu-id="777f2-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="777f2-110">Aşağıdaki çizimde, sonuçta elde edilen kesikli çizgi gösterir.</span><span class="sxs-lookup"><span data-stu-id="777f2-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="777f2-111">Böylece satırın en son 25 birimden daha kısa olacak şekilde son tire sahip unutmayın (405, 5).</span><span class="sxs-lookup"><span data-stu-id="777f2-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="777f2-112">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="777f2-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="777f2-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="777f2-113">Compiling the Code</span></span>  
 <span data-ttu-id="777f2-114">Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="777f2-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="777f2-115">Önceki kod içine yapıştırma <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="777f2-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777f2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="777f2-116">See Also</span></span>  
 [<span data-ttu-id="777f2-117">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="777f2-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
