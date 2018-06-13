---
title: 'Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: bfc40d985ec12a30b73935ace7ef034aadbd5385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522102"
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="3e79f-102">Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma</span><span class="sxs-lookup"><span data-stu-id="3e79f-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="3e79f-103">Özelliklerinden birini <xref:System.Drawing.Graphics> kırpma bölgesinin bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="3e79f-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="3e79f-104">Gerçekleştirilen tüm çizim bir verilen <xref:System.Drawing.Graphics> nesnedir, kırpma bölgesi kısıtlı <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3e79f-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3e79f-105">Kırpma bölgesinin çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3e79f-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e79f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e79f-106">Example</span></span>  
 <span data-ttu-id="3e79f-107">Aşağıdaki örnek, tek bir Çokgen oluşan bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e79f-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="3e79f-108">Ardından bu yola göre bir bölge kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e79f-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="3e79f-109">Bölge geçirilir <xref:System.Drawing.Graphics.SetClip%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi ve ardından iki dizeyi çizilir.</span><span class="sxs-lookup"><span data-stu-id="3e79f-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="3e79f-110">Aşağıdaki çizimde kırpılmış dizeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e79f-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="3e79f-111">![Küçük](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="3e79f-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e79f-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3e79f-112">Compiling the Code</span></span>  
 <span data-ttu-id="3e79f-113">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="3e79f-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e79f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e79f-114">See Also</span></span>  
 [<span data-ttu-id="3e79f-115">GDI+'daki Bölgeler</span><span class="sxs-lookup"><span data-stu-id="3e79f-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="3e79f-116">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="3e79f-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
