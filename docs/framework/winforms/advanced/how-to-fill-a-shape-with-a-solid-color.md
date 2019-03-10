---
title: 'Nasıl yapılır: Bir şekli düz renk ile doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: 8bc782f9496a9c1562bad2df1ba196fb39572e68
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704456"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="58058-102">Nasıl yapılır: Bir şekli düz renk ile doldurma</span><span class="sxs-lookup"><span data-stu-id="58058-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="58058-103">Bir şekli düz renk ile doldurma için oluşturma bir <xref:System.Drawing.SolidBrush> nesnesi ve ardından, geçirin <xref:System.Drawing.SolidBrush> dolgu yöntemlerinden birini bağımsız değişkeni olarak bir nesne <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="58058-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="58058-104">Aşağıdaki örnek, bir elips kırmızı renkle doldurma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58058-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58058-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="58058-105">Example</span></span>  
 <span data-ttu-id="58058-106">Aşağıdaki kodda, <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu alır bir <xref:System.Drawing.Color> yalnızca bağımsız değişken olarak nesnesi.</span><span class="sxs-lookup"><span data-stu-id="58058-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="58058-107">Tarafından kullanılan değerleri <xref:System.Drawing.Color.FromArgb%2A> yöntemi alfa, kırmızı, yeşil ve mavi renk bileşenleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58058-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="58058-108">Bu değerlerin her birini, 0-255 aralığında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58058-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="58058-109">İlk 255 rengi ila tamamen opak ve ikinci 255 kırmızı bileşeni tam yoğunlukta gösterir gösterir.</span><span class="sxs-lookup"><span data-stu-id="58058-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="58058-110">İki sıfır, yeşil ve mavi bileşenlerinin bir yoğunluğu 0 olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="58058-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="58058-111">Dört rakam (0, 0, 100, 60) geçirilen <xref:System.Drawing.Graphics.FillEllipse%2A> elipsin dikdörtgen boyutunu ve konumunu yöntemini belirtin.</span><span class="sxs-lookup"><span data-stu-id="58058-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="58058-112">Dikdörtgen bir sol üst köşesinde sahiptir (0, 0), bir 100 genişlik ve yükseklik 60'a.</span><span class="sxs-lookup"><span data-stu-id="58058-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58058-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="58058-113">Compiling the Code</span></span>  
 <span data-ttu-id="58058-114">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="58058-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58058-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58058-115">See also</span></span>
- [<span data-ttu-id="58058-116">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="58058-116">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
