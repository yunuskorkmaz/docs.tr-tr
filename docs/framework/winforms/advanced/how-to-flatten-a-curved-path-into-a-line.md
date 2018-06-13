---
title: 'Nasıl yapılır: Eğik bir Yolu Düzleştirerek Çizgiye Dönüştürme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a3a8467dc5906a88911672316bb0f2ed3607d3a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521209"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="db259-102">Nasıl yapılır: Eğik bir Yolu Düzleştirerek Çizgiye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="db259-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="db259-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi bir dizi satırları ve Bézier eğrileri saklar.</span><span class="sxs-lookup"><span data-stu-id="db259-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="db259-104">Bir yol Eğriler (üç nokta, yaylar, eğriler) çeşitli türlerde ekleyebilirsiniz ancak yolunda saklanan önce her eğri bir Bézier eğrisi dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="db259-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="db259-105">Bir yol düzleştirme bir dizi düz satır yolundaki her bir Bézier eğrisi dönüştürme oluşur.</span><span class="sxs-lookup"><span data-stu-id="db259-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="db259-106">Aşağıdaki çizimde, önce ve sonra düzleştirme bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="db259-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="db259-107">![Düz çizgiler ve eğrilerle](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="db259-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="db259-108">Bir yolu düzleştirerek için</span><span class="sxs-lookup"><span data-stu-id="db259-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="db259-109">çağrı <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> yöntemi bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="db259-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="db259-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Yöntemi düzleştirilmiş yol ve özgün yol arasındaki maksimum mesafeyi belirtir düzlük bağımsız değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="db259-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db259-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db259-111">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [<span data-ttu-id="db259-112">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="db259-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="db259-113">Yollar Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="db259-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
