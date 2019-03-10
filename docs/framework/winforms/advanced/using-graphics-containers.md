---
title: Grafik Kapsayıcıları Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704498"
---
# <a name="using-graphics-containers"></a><span data-ttu-id="1523f-102">Grafik Kapsayıcıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1523f-102">Using Graphics Containers</span></span>
<span data-ttu-id="1523f-103">A <xref:System.Drawing.Graphics> nesne yöntemleri gibi sağlar <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, ve <xref:System.Drawing.Graphics.DrawString%2A> vektör görüntüleri, tarama görüntü ve metin gösterme.</span><span class="sxs-lookup"><span data-stu-id="1523f-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="1523f-104">A <xref:System.Drawing.Graphics> nesne çizilir öğeleri yönünü ve kalite etkileyen çeşitli özellikleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="1523f-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="1523f-105">Örneğin, yumuşatma modu özelliği için çizgiler ve eğrilerle düzgünleştirme uygulanır ve konum ve döndürme çizilir öğelerinin dünya dönüştürme özelliğini etkiler olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1523f-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="1523f-106">A <xref:System.Drawing.Graphics> nesne belirli bir görüntü cihazı ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="1523f-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="1523f-107">Kullandığınızda, bir <xref:System.Drawing.Graphics> bir pencerede çizmek için nesne <xref:System.Drawing.Graphics> nesnedir Ayrıca, belirli bir pencere ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="1523f-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="1523f-108">A <xref:System.Drawing.Graphics> nesne düşünülebilir bir kapsayıcı gibi çizim etkileyen özellikler kümesi tutmadığından ve cihaza özgü bilgiler için bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1523f-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="1523f-109">İçinde mevcut bir ikincil bir kapsayıcı oluşturduğunuz <xref:System.Drawing.Graphics> çağırarak <xref:System.Drawing.Graphics.BeginContainer%2A> yöntem <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1523f-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1523f-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1523f-110">In This Section</span></span>  
 [<span data-ttu-id="1523f-111">Bir Grafik Nesnesinin Durumunu Yönetme</span><span class="sxs-lookup"><span data-stu-id="1523f-111">Managing the State of a Graphics Object</span></span>](managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="1523f-112">Açıklar kalite ayarları, kırpma alan ve dönüşümleri yönetme bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1523f-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="1523f-113">İç İçe Grafik Kapsayıcılarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1523f-113">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)  
 <span data-ttu-id="1523f-114">Durumu denetlemek için kapsayıcıları kullanmayı gösterir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1523f-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
