---
title: Eğriler Oluşturma ve Çizme
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 92e7b1e8b4ce37db633b5dafe212a252b854d1af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935453"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="2d484-102">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="2d484-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2d484-103">eğrileri çeşitli türlerini destekler: üç nokta, yay, eğriler ve Bézier eğrileri.</span><span class="sxs-lookup"><span data-stu-id="2d484-103">supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="2d484-104">Bir elips, sınırlayıcı dikdörtgeni tarafından tanımlanır; Yay Başlangıç açısı ve bir tarama açısı tarafından tanımlanan bir elips bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="2d484-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="2d484-105">Kardinal eğri, bir dizi noktaları ve gerilimi parametresi tarafından tanımlanır; eğri dizideki her noktası sorunsuz geçtiği ve gerilimi parametre bends eğrinin şeklini etkiler.</span><span class="sxs-lookup"><span data-stu-id="2d484-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="2d484-106">Bézier eğri iki uç nokta ve iki denetim noktaları eğri denetim noktaları üzerinden geçmez tanımlanır, ancak denetim noktaları yönünü etkiler ve eğri bir uç noktasından diğerine geçebileceği Kıvrım.</span><span class="sxs-lookup"><span data-stu-id="2d484-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d484-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2d484-107">In This Section</span></span>  
 [<span data-ttu-id="2d484-108">Nasıl yapılır: Eğriler çizme</span><span class="sxs-lookup"><span data-stu-id="2d484-108">How to: Draw Cardinal Splines</span></span>](how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="2d484-109">Kardinal eğrileri ve bunları nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="2d484-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="2d484-110">Nasıl yapılır: Tek bir Bézier eğri çizme</span><span class="sxs-lookup"><span data-stu-id="2d484-110">How to: Draw a Single Bézier Spline</span></span>](how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="2d484-111">Bézier eğri ve tek tek açıklar.</span><span class="sxs-lookup"><span data-stu-id="2d484-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="2d484-112">Nasıl yapılır: Bir dizi Bézier eğrileri çizme</span><span class="sxs-lookup"><span data-stu-id="2d484-112">How to: Draw a Sequence of Bézier Splines</span></span>](how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="2d484-113">Sırayla birkaç Bézier eğrileri çizmek kullanılan nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d484-113">Explains how to draw several Bézier splines in sequence.</span></span>
