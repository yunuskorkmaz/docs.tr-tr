---
title: "Nasıl yapılır: Bir Şekli Düz Renk ile Doldurma"
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
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f016404feeac47c5f77527b8baa68d70742d4763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="1e117-102">Nasıl yapılır: Bir Şekli Düz Renk ile Doldurma</span><span class="sxs-lookup"><span data-stu-id="1e117-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="1e117-103">Bir şekli düz renk ile doldurma için oluşturun bir <xref:System.Drawing.SolidBrush> nesne ve daha sonra geçirin <xref:System.Drawing.SolidBrush> nesnesi dolgu yöntemlerinden birini bağımsız değişken olarak <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1e117-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="1e117-104">Aşağıdaki örnek, bir elips dolgu rengi kırmızı ile gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e117-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e117-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e117-105">Example</span></span>  
 <span data-ttu-id="1e117-106">Aşağıdaki kodda, <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu geçen bir <xref:System.Drawing.Color> nesnesi yalnızca bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="1e117-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="1e117-107">Tarafından kullanılan değerleri <xref:System.Drawing.Color.FromArgb%2A> yöntemi rengi alfa, kırmızı, yeşil ve mavi bileşenlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e117-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="1e117-108">Bu değerlerin her birini 0 ile 255 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e117-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="1e117-109">İlk 255 rengi tamamıyla opak ve ikinci 255 kırmızı bileşenini tam yoğunlukta gösterir gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e117-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="1e117-110">Yeşil ve mavi bileşenleri bir yoğunluğu 0 olan iki sıfır belirtin.</span><span class="sxs-lookup"><span data-stu-id="1e117-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="1e117-111">Dört rakam (0, 0, 100, 60) geçirilen <xref:System.Drawing.Graphics.FillEllipse%2A> yöntemi elips için sınırlayıcı dikdörtgenini boyutunu ve konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="1e117-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="1e117-112">Dikdörtgen bir sol üst köşesindeki sahip (0, 0), 100 genişliğini bir ve 60 yüksekliğini bir.</span><span class="sxs-lookup"><span data-stu-id="1e117-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e117-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1e117-113">Compiling the Code</span></span>  
 <span data-ttu-id="1e117-114">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1e117-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e117-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e117-115">See Also</span></span>  
 [<span data-ttu-id="1e117-116">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="1e117-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
