---
title: 'Nasıl yapılır: Satırları Birleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 445d7f12f57137c6b06a074eeaf0574eb027a723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174921"
---
# <a name="how-to-join-lines"></a><span data-ttu-id="1945a-102">Nasıl yapılır: Satırları Birleştirme</span><span class="sxs-lookup"><span data-stu-id="1945a-102">How to: Join Lines</span></span>
<span data-ttu-id="1945a-103">Satır birleştirme, sona erer karşılamak ya da üst üste iki satırla ayrılan biçimlendirilmiş ortak bir alandır.</span><span class="sxs-lookup"><span data-stu-id="1945a-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="1945a-104">üç çizgi birleştirme stili sağlar: gönye, eğim ve yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="1945a-104">provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="1945a-105">Çizgisi birleştirme stili bir özelliği olan <xref:System.Drawing.Pen> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1945a-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="1945a-106">Bir çizgi birleştirme stili belirttiğinizde bir <xref:System.Drawing.Pen> nesnesi, birleştirme stili herhangi bağlı tüm satırlara uygulanacak <xref:System.Drawing.Drawing2D.GraphicsPath> , kalem kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="1945a-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="1945a-107">Aşağıdaki çizim, eğik çizgi birleştirme örnek sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1945a-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 ![Çizim Birleştirilmiş satırları gösterir.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a><span data-ttu-id="1945a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1945a-109">Example</span></span>  
 <span data-ttu-id="1945a-110">Kullanarak çizgisi birleştirme stili belirtebilirsiniz <xref:System.Drawing.Pen.LineJoin%2A> özelliği <xref:System.Drawing.Pen> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1945a-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="1945a-111">Örnek bir eğik çizgi birleştirme yatay çizgi dikey çizgi arasındaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="1945a-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="1945a-112">Aşağıdaki kodda, değer <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atanan <xref:System.Drawing.Pen.LineJoin%2A> özelliği üyesi olduğu <xref:System.Drawing.Drawing2D.LineJoin> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1945a-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="1945a-113">Diğer üyeleri <xref:System.Drawing.Drawing2D.LineJoin> numaralandırma olan <xref:System.Drawing.Drawing2D.LineJoin.Miter> ve <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="1945a-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1945a-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1945a-114">Compiling the Code</span></span>  
 <span data-ttu-id="1945a-115">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1945a-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1945a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1945a-116">See also</span></span>

- [<span data-ttu-id="1945a-117">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="1945a-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
