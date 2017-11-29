---
title: "Çizgiler ve Şekiller Çizmek için Kalem Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0913dc2745e1b244e4b03c0e6b946441a401c5b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="6dee9-102">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="6dee9-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="6dee9-103">Kullanım [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` çizgi dilimleri, eğriler ve şekiller anahatları çizmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6dee9-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="6dee9-104">Bu bölümde *satır* herhangi birinde, yalnızca bir çizgi kesimi anlamına gelir belirtilmediği sürece başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="6dee9-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="6dee9-105">Bir kalemin rengini, genişliğini, hizalama ve o kalem ile çizilmiş çizgi stilini denetlemek için özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6dee9-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6dee9-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6dee9-106">In This Section</span></span>  
 [<span data-ttu-id="6dee9-107">Nasıl yapılır: çizgi çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="6dee9-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="6dee9-108">Çizgiler çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6dee9-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="6dee9-109">Nasıl yapılır: dikdörtgen çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="6dee9-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="6dee9-110">Dikdörtgenler çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="6dee9-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="6dee9-111">Nasıl yapılır: Kalem genişliği ve hizalamasını ayarlama</span><span class="sxs-lookup"><span data-stu-id="6dee9-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="6dee9-112">Genişliği ve hizalamasını nasıl değiştirileceğini açıklar bir `Pen` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6dee9-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="6dee9-113">Nasıl yapılır: çizgi uçlarıyla çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="6dee9-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="6dee9-114">Bir satır çizerken uç başlıkları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6dee9-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="6dee9-115">Nasıl yapılır: çizgileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="6dee9-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="6dee9-116">İki satır nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dee9-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="6dee9-117">Nasıl yapılır: özel kesikli çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="6dee9-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="6dee9-118">Kesikli çizgi çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="6dee9-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="6dee9-119">Nasıl yapılır: bir dokuyla doldurulmuş çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="6dee9-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="6dee9-120">Doku doldurulmuş çizgi çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6dee9-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6dee9-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6dee9-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="6dee9-122">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="6dee9-122">Describes this class and has links to all its members.</span></span>
