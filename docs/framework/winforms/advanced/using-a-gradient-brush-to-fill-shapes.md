---
title: Şekilleri Doldurmak için Gradyan Fırçası Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 5771aaabd283d71f5fa6934f86a1c24a57f38dca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954472"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="9c561-102">Şekilleri Doldurmak için Gradyan Fırçası Kullanma</span><span class="sxs-lookup"><span data-stu-id="9c561-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="9c561-103">Bir şekli bir yavaş yavaş değişen rengi ile doldurmak için gradyan fırçası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c561-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="9c561-104">Örneğin, bir şekli olarak şeklin sol kenardan sağ kenarına taşıyın, yavaş yavaş değişen renk ile doldurma için Yatay Gradyan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c561-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="9c561-105">Siyah bir sol kenarı ile bir dikdörtgen Imagine (kırmızı, yeşil ve mavi bileşenleriyle belirtildiği 0, 0, 0) ve bir sağ kenar diğer bir deyişle kırmızı (255, 0, 0 tarafından gösterilen).</span><span class="sxs-lookup"><span data-stu-id="9c561-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="9c561-106">256 piksel genişliğinde dikdörtgen ise kırmızı bileşeni belirli bir pikselin bir pikselin solunda kırmızı bileşeni büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9c561-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="9c561-107">Bir satırdaki en soldaki piksel renk bileşeni (0, 0, 0) sahip, ikinci piksel olan (1, 0, 0), üçüncü piksel (2, 0, 0) sahip vb. (255, 0, 0) renk bileşenleri en sağdaki piksel gelene kadar.</span><span class="sxs-lookup"><span data-stu-id="9c561-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="9c561-108">Bu ilişkilendirilmiş renk değerleri renk gradyanı olun.</span><span class="sxs-lookup"><span data-stu-id="9c561-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="9c561-109">Yatay, dikey taşıdığınızda veya belirli bir Eğimli satırını paralel olarak doğrusal gradyan rengini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9c561-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="9c561-110">İç ve bir yol sınırları hakkında hareket yolu gradyan rengini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9c561-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="9c561-111">Yol gradyanları çok çeşitli efektler elde etmek için özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c561-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="9c561-112">Doğrusal gradyan fırçası ile bir dikdörtgen doldurulmuş ve yolun gradyan fırçası ile bir elips doldurulmuş aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9c561-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="9c561-113">![Gradyan](./media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="9c561-113">![Gradient](./media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c561-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9c561-114">In This Section</span></span>  
 [<span data-ttu-id="9c561-115">Nasıl yapılır: Doğrusal gradyan oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c561-115">How to: Create a Linear Gradient</span></span>](how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="9c561-116">Bir doğrusal gradyan kullanarak oluşturulacağını gösterir <xref:System.Drawing.Drawing2D.LinearGradientBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9c561-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="9c561-117">Nasıl yapılır: Yol gradyanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c561-117">How to: Create a Path Gradient</span></span>](how-to-create-a-path-gradient.md)  
 <span data-ttu-id="9c561-118">Kullanarak bir yol gradyanı oluşturma işlemini açıklamaktadır <xref:System.Drawing.Drawing2D.PathGradientBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9c561-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="9c561-119">Nasıl yapılır: Bir Gradyana gama düzeltmesi uygulama</span><span class="sxs-lookup"><span data-stu-id="9c561-119">How to: Apply Gamma Correction to a Gradient</span></span>](how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="9c561-120">Gradyan fırça gama düzeltmesi kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9c561-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9c561-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9c561-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="9c561-122">Bu sınıfın bir açıklama içerir ve tüm üyelerini bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="9c561-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="9c561-123">Bu sınıfın bir açıklama içerir ve tüm üyelerini bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="9c561-123">Contains a description of this class and has links to all of its members.</span></span>
