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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777253"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="af529-102">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="af529-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="af529-103">Kullanım [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` nesnelerinin çizgi segmentleri, eğriler ve şekiller anahatlarını çizmek için.</span><span class="sxs-lookup"><span data-stu-id="af529-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="af529-104">Bu bölümde, *satırı* bunlardan birine yalnızca bir çizgi kesimi auto'yu belirtilmediği sürece ifade eder.</span><span class="sxs-lookup"><span data-stu-id="af529-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="af529-105">Kalem rengi, genişlik, hizalama ve o kalem ile çizilen çizgi stilini denetlemek için özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="af529-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af529-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="af529-106">In This Section</span></span>  
 [<span data-ttu-id="af529-107">Nasıl yapılır: Çizgi çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="af529-107">How to: Use a Pen to Draw Lines</span></span>](how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="af529-108">Çizgi çizmek kullanılan nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af529-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="af529-109">Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="af529-109">How to: Use a Pen to Draw Rectangles</span></span>](how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="af529-110">Dikdörtgen çizmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="af529-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="af529-111">Nasıl yapılır: Kümesi kalem genişliği ve hizalamasını</span><span class="sxs-lookup"><span data-stu-id="af529-111">How to: Set Pen Width and Alignment</span></span>](how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="af529-112">Genişliğini ve hizalamasını değiştirme açıklayan bir `Pen` nesne.</span><span class="sxs-lookup"><span data-stu-id="af529-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="af529-113">Nasıl yapılır: Çizgi uçlarıyla çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="af529-113">How to: Draw a Line with Line Caps</span></span>](how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="af529-114">Bir satır çizerken uç başlıkları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="af529-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="af529-115">Nasıl yapılır: Satırları birleştirme</span><span class="sxs-lookup"><span data-stu-id="af529-115">How to: Join Lines</span></span>](how-to-join-lines.md)  
 <span data-ttu-id="af529-116">İki satır birleştirme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af529-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="af529-117">Nasıl yapılır: Özel kesikli çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="af529-117">How to: Draw a Custom Dashed Line</span></span>](how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="af529-118">Kesikli çizgi çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="af529-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="af529-119">Nasıl yapılır: Bir dokuyla doldurulmuş çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="af529-119">How to: Draw a Line Filled with a Texture</span></span>](how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="af529-120">Doku doldurulmuş çizgi çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af529-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="af529-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="af529-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="af529-122">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="af529-122">Describes this class and has links to all its members.</span></span>
