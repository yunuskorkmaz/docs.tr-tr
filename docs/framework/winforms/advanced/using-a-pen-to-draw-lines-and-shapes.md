---
title: Çizgiler ve Şekiller Çizmek için Kalem Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
ms.openlocfilehash: d20b4e47c9f8a5dd7a144e6ebb3151d3ab65a800
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505145"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="1cbe2-102">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cbe2-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="1cbe2-103">GDI + kullanma `Pen` nesnelerinin çizgi segmentleri, eğriler ve şekiller anahatlarını çizmek için.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-103">Use GDI+ `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="1cbe2-104">Bu bölümde, *satırı* bunlardan birine yalnızca bir çizgi kesimi auto'yu belirtilmediği sürece ifade eder.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="1cbe2-105">Kalem rengi, genişlik, hizalama ve o kalem ile çizilen çizgi stilini denetlemek için özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cbe2-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1cbe2-106">In This Section</span></span>  
 [<span data-ttu-id="1cbe2-107">Nasıl yapılır: Çizgi çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="1cbe2-107">How to: Use a Pen to Draw Lines</span></span>](how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="1cbe2-108">Çizgi çizmek kullanılan nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="1cbe2-109">Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="1cbe2-109">How to: Use a Pen to Draw Rectangles</span></span>](how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="1cbe2-110">Dikdörtgen çizmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="1cbe2-111">Nasıl yapılır: Kümesi kalem genişliği ve hizalamasını</span><span class="sxs-lookup"><span data-stu-id="1cbe2-111">How to: Set Pen Width and Alignment</span></span>](how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="1cbe2-112">Genişliğini ve hizalamasını değiştirme açıklayan bir `Pen` nesne.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="1cbe2-113">Nasıl yapılır: Çizgi uçlarıyla çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="1cbe2-113">How to: Draw a Line with Line Caps</span></span>](how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="1cbe2-114">Bir satır çizerken uç başlıkları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="1cbe2-115">Nasıl yapılır: Satırları birleştirme</span><span class="sxs-lookup"><span data-stu-id="1cbe2-115">How to: Join Lines</span></span>](how-to-join-lines.md)  
 <span data-ttu-id="1cbe2-116">İki satır birleştirme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="1cbe2-117">Nasıl yapılır: Özel kesikli çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="1cbe2-117">How to: Draw a Custom Dashed Line</span></span>](how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="1cbe2-118">Kesikli çizgi çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="1cbe2-119">Nasıl yapılır: Bir dokuyla doldurulmuş çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="1cbe2-119">How to: Draw a Line Filled with a Texture</span></span>](how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="1cbe2-120">Doku doldurulmuş çizgi çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1cbe2-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1cbe2-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="1cbe2-122">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="1cbe2-122">Describes this class and has links to all its members.</span></span>
