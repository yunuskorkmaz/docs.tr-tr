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
ms.openlocfilehash: d59a802618ddd5080c651e822ed4c09641f7f170
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645359"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="63a54-102">Nasıl yapılır: Eğik bir Yolu Düzleştirerek Çizgiye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="63a54-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="63a54-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi bir dizi satır ve Bézier eğrileri depolar.</span><span class="sxs-lookup"><span data-stu-id="63a54-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="63a54-104">Eğrileri (elips yaylar, ana Eğriler) birkaç türde bir yola ekleyebilirsiniz, ancak yolda depolanmadan önce her eğrisinin bir Bézier eğri için dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="63a54-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="63a54-105">Düzleştirme bir yol dizisi düz çizgiler ile yoldaki her Bézier eğri dönüştürme oluşur.</span><span class="sxs-lookup"><span data-stu-id="63a54-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="63a54-106">Aşağıdaki çizim, önce ve sonra düzleştirme bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="63a54-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="63a54-107">![Düz çizgiler ve eğrilerle](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="63a54-107">![Straight Lines and Curves](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="63a54-108">Bir yol düzleştirmek için</span><span class="sxs-lookup"><span data-stu-id="63a54-108">To Flatten a Path</span></span>  
  
- <span data-ttu-id="63a54-109">çağrı <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> yöntemi bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne.</span><span class="sxs-lookup"><span data-stu-id="63a54-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="63a54-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Yöntem düzleştirilmiş ile özgün yolu arasında en fazla mesafe belirten bir düzlük bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="63a54-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a54-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63a54-111">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [<span data-ttu-id="63a54-112">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="63a54-112">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="63a54-113">Yollar Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="63a54-113">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
