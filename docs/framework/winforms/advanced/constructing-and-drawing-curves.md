---
title: "Eğriler Oluşturma ve Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 801af10f7b9e5e7998fc061537977c5bced6bdb3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="96eff-102">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="96eff-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="96eff-103">Eğriler çeşitli türlerini destekler: üç nokta, yaylar, eğriler ve Bézier eğrisi.</span><span class="sxs-lookup"><span data-stu-id="96eff-103"> supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="96eff-104">Elips kendisini çevreleyen bir dikdörtgen tarafından tanımlanan; Yayı Başlangıç açısı ve bir tarama açısı tarafından tanımlanan bir elips bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="96eff-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="96eff-105">Kardinal eğri noktası ve gerilim parametre dizisi tarafından tanımlanan — eğri her bir dizi noktası sorunsuz geçtiği ve gerilim parametre eğri bends biçimini etkiler.</span><span class="sxs-lookup"><span data-stu-id="96eff-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="96eff-106">Bir Bézier eğrisi iki uç nokta ile eğri denetim noktaları aracılığıyla iletmez iki denetim noktaları tarafından tanımlanan, ancak denetim noktaları yönde etkileyen ve eğri bir uç noktasından diğerine geçtikçe bükme.</span><span class="sxs-lookup"><span data-stu-id="96eff-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96eff-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="96eff-107">In This Section</span></span>  
 [<span data-ttu-id="96eff-108">Nasıl yapılır: Eğriler çizme</span><span class="sxs-lookup"><span data-stu-id="96eff-108">How to: Draw Cardinal Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="96eff-109">Ana eğriler ve çizerken açıklar.</span><span class="sxs-lookup"><span data-stu-id="96eff-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="96eff-110">Nasıl yapılır: tek bir Bézier eğrisi çizme</span><span class="sxs-lookup"><span data-stu-id="96eff-110">How to: Draw a Single Bézier Spline</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="96eff-111">Bir Bézier eğrisi ve tek tek açıklar.</span><span class="sxs-lookup"><span data-stu-id="96eff-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="96eff-112">Nasıl yapılır: bir sıra Bézier eğrisi çizme</span><span class="sxs-lookup"><span data-stu-id="96eff-112">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="96eff-113">Sırayla birkaç Bézier eğrisi çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96eff-113">Explains how to draw several Bézier splines in sequence.</span></span>
