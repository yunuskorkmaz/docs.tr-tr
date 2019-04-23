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
ms.openlocfilehash: cf60b32df805a49f8da2760332dc32e34209f6dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163741"
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="4225e-102">Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma</span><span class="sxs-lookup"><span data-stu-id="4225e-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="4225e-103">Özelliklerinden birini <xref:System.Drawing.Graphics> kırpma bölgesini sınıftır.</span><span class="sxs-lookup"><span data-stu-id="4225e-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="4225e-104">Tüm çizim tarafından bir verilen <xref:System.Drawing.Graphics> nesnedir, söz konusu küçük bölgesiyle sınırlı <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="4225e-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="4225e-105">Kırpma bölgesini çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4225e-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4225e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4225e-106">Example</span></span>  
 <span data-ttu-id="4225e-107">Aşağıdaki örnek tek bir Çokgen oluşan bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4225e-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="4225e-108">Ardından bu yola göre bir bölge kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4225e-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="4225e-109">Bölge geçirilir <xref:System.Drawing.Graphics.SetClip%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi ve ardından iki dizeyi çizilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4225e-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="4225e-110">Aşağıdaki çizim, kırpılmış dizelerden gösterir.</span><span class="sxs-lookup"><span data-stu-id="4225e-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="4225e-111">![Küçük](./media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="4225e-111">![Clip](./media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4225e-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4225e-112">Compiling the Code</span></span>  
 <span data-ttu-id="4225e-113">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="4225e-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4225e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4225e-114">See also</span></span>

- [<span data-ttu-id="4225e-115">GDI+'daki Bölgeler</span><span class="sxs-lookup"><span data-stu-id="4225e-115">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="4225e-116">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="4225e-116">Using Regions</span></span>](using-regions.md)
