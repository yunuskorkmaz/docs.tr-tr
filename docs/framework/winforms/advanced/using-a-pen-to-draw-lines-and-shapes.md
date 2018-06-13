---
title: Çizgiler ve Şekiller Çizmek için Kalem Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
ms.openlocfilehash: 667a5b13c5e8cb5d9a693d6f8512b254f130d606
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524348"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="6f5e4-102">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="6f5e4-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="6f5e4-103">Kullanım [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` çizgi dilimleri, eğriler ve şekiller anahatları çizmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="6f5e4-104">Bu bölümde *satır* herhangi birinde, yalnızca bir çizgi kesimi anlamına gelir belirtilmediği sürece başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="6f5e4-105">Bir kalemin rengini, genişliğini, hizalama ve o kalem ile çizilmiş çizgi stilini denetlemek için özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f5e4-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6f5e4-106">In This Section</span></span>  
 [<span data-ttu-id="6f5e4-107">Nasıl yapılır: Çizgi Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="6f5e4-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="6f5e4-108">Çizgiler çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="6f5e4-109">Nasıl yapılır: Dikdörtgen Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="6f5e4-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="6f5e4-110">Dikdörtgenler çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="6f5e4-111">Nasıl yapılır: Kalem Genişliği ve Hizalamasını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f5e4-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="6f5e4-112">Genişliği ve hizalamasını nasıl değiştirileceğini açıklar bir `Pen` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="6f5e4-113">Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="6f5e4-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="6f5e4-114">Bir satır çizerken uç başlıkları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="6f5e4-115">Nasıl yapılır: Çizgileri Birleştirme</span><span class="sxs-lookup"><span data-stu-id="6f5e4-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="6f5e4-116">İki satır nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="6f5e4-117">Nasıl yapılır: Özel Kesikli Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="6f5e4-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="6f5e4-118">Kesikli çizgi çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="6f5e4-119">Nasıl yapılır: Bir Dokuyla Doldurulmuş Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="6f5e4-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="6f5e4-120">Doku doldurulmuş çizgi çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6f5e4-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6f5e4-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="6f5e4-122">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="6f5e4-122">Describes this class and has links to all its members.</span></span>
