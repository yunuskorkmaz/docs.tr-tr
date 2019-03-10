---
title: Çizgiler ve Şekiller Çizmek için Kalem Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
ms.openlocfilehash: 3846c59712cec6003c35f336714041544dec94b3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716299"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="103fe-102">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="103fe-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="103fe-103">Kullanım [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` nesnelerinin çizgi segmentleri, eğriler ve şekiller anahatlarını çizmek için.</span><span class="sxs-lookup"><span data-stu-id="103fe-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="103fe-104">Bu bölümde, *satırı* bunlardan birine yalnızca bir çizgi kesimi auto'yu belirtilmediği sürece ifade eder.</span><span class="sxs-lookup"><span data-stu-id="103fe-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="103fe-105">Kalem rengi, genişlik, hizalama ve o kalem ile çizilen çizgi stilini denetlemek için özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="103fe-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="103fe-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="103fe-106">In This Section</span></span>  
 [<span data-ttu-id="103fe-107">Nasıl yapılır: Çizgi çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="103fe-107">How to: Use a Pen to Draw Lines</span></span>](how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="103fe-108">Çizgi çizmek kullanılan nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="103fe-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="103fe-109">Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="103fe-109">How to: Use a Pen to Draw Rectangles</span></span>](how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="103fe-110">Dikdörtgen çizmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="103fe-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="103fe-111">Nasıl yapılır: Kümesi kalem genişliği ve hizalamasını</span><span class="sxs-lookup"><span data-stu-id="103fe-111">How to: Set Pen Width and Alignment</span></span>](how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="103fe-112">Genişliğini ve hizalamasını değiştirme açıklayan bir `Pen` nesne.</span><span class="sxs-lookup"><span data-stu-id="103fe-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="103fe-113">Nasıl yapılır: Çizgi uçlarıyla çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="103fe-113">How to: Draw a Line with Line Caps</span></span>](how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="103fe-114">Bir satır çizerken uç başlıkları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="103fe-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="103fe-115">Nasıl yapılır: Satırları birleştirme</span><span class="sxs-lookup"><span data-stu-id="103fe-115">How to: Join Lines</span></span>](how-to-join-lines.md)  
 <span data-ttu-id="103fe-116">İki satır birleştirme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="103fe-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="103fe-117">Nasıl yapılır: Özel kesikli çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="103fe-117">How to: Draw a Custom Dashed Line</span></span>](how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="103fe-118">Kesikli çizgi çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="103fe-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="103fe-119">Nasıl yapılır: Bir dokuyla doldurulmuş çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="103fe-119">How to: Draw a Line Filled with a Texture</span></span>](how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="103fe-120">Doku doldurulmuş çizgi çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="103fe-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="103fe-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="103fe-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="103fe-122">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="103fe-122">Describes this class and has links to all its members.</span></span>
