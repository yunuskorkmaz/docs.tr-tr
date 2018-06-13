---
title: Eğriler Oluşturma ve Çizme
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: d9a790060fdf0f0c2a739d99aba1b36cf0323f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520623"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="03f7b-102">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="03f7b-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="03f7b-103"> Eğriler çeşitli türlerini destekler: üç nokta, yaylar, eğriler ve Bézier eğrisi.</span><span class="sxs-lookup"><span data-stu-id="03f7b-103"> supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="03f7b-104">Elips kendisini çevreleyen bir dikdörtgen tarafından tanımlanan; Yayı Başlangıç açısı ve bir tarama açısı tarafından tanımlanan bir elips bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="03f7b-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="03f7b-105">Kardinal eğri noktası ve gerilim parametre dizisi tarafından tanımlanan — eğri her bir dizi noktası sorunsuz geçtiği ve gerilim parametre eğri bends biçimini etkiler.</span><span class="sxs-lookup"><span data-stu-id="03f7b-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="03f7b-106">Bir Bézier eğrisi iki uç nokta ile eğri denetim noktaları aracılığıyla iletmez iki denetim noktaları tarafından tanımlanan, ancak denetim noktaları yönde etkileyen ve eğri bir uç noktasından diğerine geçtikçe bükme.</span><span class="sxs-lookup"><span data-stu-id="03f7b-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03f7b-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="03f7b-107">In This Section</span></span>  
 [<span data-ttu-id="03f7b-108">Nasıl yapılır: Ana Eğriler Çizme</span><span class="sxs-lookup"><span data-stu-id="03f7b-108">How to: Draw Cardinal Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="03f7b-109">Ana eğriler ve çizerken açıklar.</span><span class="sxs-lookup"><span data-stu-id="03f7b-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="03f7b-110">Nasıl yapılır: Tek Bir Bézier Eğrisi Çizme</span><span class="sxs-lookup"><span data-stu-id="03f7b-110">How to: Draw a Single Bézier Spline</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="03f7b-111">Bir Bézier eğrisi ve tek tek açıklar.</span><span class="sxs-lookup"><span data-stu-id="03f7b-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="03f7b-112">Nasıl yapılır: Bir Sıra Bézier Eğrisi Çizme</span><span class="sxs-lookup"><span data-stu-id="03f7b-112">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="03f7b-113">Sırayla birkaç Bézier eğrisi çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03f7b-113">Explains how to draw several Bézier splines in sequence.</span></span>
