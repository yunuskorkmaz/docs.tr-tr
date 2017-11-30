---
title: "Grafik Kapsayıcıları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 337057e10e03712aa93b00d9c687374e53f8dd03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="using-graphics-containers"></a><span data-ttu-id="b6c70-102">Grafik Kapsayıcıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b6c70-102">Using Graphics Containers</span></span>
<span data-ttu-id="b6c70-103">A <xref:System.Drawing.Graphics> nesnesi sağlar yöntemleri gibi <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, ve <xref:System.Drawing.Graphics.DrawString%2A> vektör görüntüleri, ızgara görüntüleri ve metin görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="b6c70-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="b6c70-104">A <xref:System.Drawing.Graphics> nesne kalitesini ve çizilir öğeleri yönünü etkileyen çeşitli özellikler de vardır.</span><span class="sxs-lookup"><span data-stu-id="b6c70-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="b6c70-105">Örneğin, yumuşatma modu özelliği çizgiler ve eğrilerle düzgünleştirme uygulanır ve dünya dönüşümü özelliği konum ve dönüş çizilir öğelerinin etkilediğini olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="b6c70-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="b6c70-106">A <xref:System.Drawing.Graphics> nesne belirli görüntüleme cihazı ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="b6c70-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="b6c70-107">Kullandığınızda, bir <xref:System.Drawing.Graphics> bir pencerede çizmek için nesne <xref:System.Drawing.Graphics> nesne bu belirli pencere ile ilişkili değil de.</span><span class="sxs-lookup"><span data-stu-id="b6c70-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="b6c70-108">A <xref:System.Drawing.Graphics> nesne zorlayıcı bir kapsayıcı olarak çizim etkileyen özellikler kümesi tutan olduğundan ve cihaza özgü bilgileri bağlı.</span><span class="sxs-lookup"><span data-stu-id="b6c70-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="b6c70-109">Var olan içindeki ikincil bir kapsayıcı oluşturabilirsiniz <xref:System.Drawing.Graphics> çağırarak nesne <xref:System.Drawing.Graphics.BeginContainer%2A> yöntemi, <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b6c70-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6c70-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b6c70-110">In This Section</span></span>  
 [<span data-ttu-id="b6c70-111">Bir grafik nesnesinin durumunu yönetme</span><span class="sxs-lookup"><span data-stu-id="b6c70-111">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="b6c70-112">Açıklar kalitesi ayarları, kırpma alanı ve dönüşümleri, nasıl yönettiğini bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b6c70-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="b6c70-113">İç içe grafik kapsayıcılarını kullanma</span><span class="sxs-lookup"><span data-stu-id="b6c70-113">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 <span data-ttu-id="b6c70-114">Kapsayıcıları durumunu denetlemek için nasıl kullanılacağını gösterir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b6c70-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
