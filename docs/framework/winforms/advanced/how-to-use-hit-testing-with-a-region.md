---
title: 'Nasıl yapılır: Test bir bölgeyle vuruş kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: a9435724e7674fd196ad70bdfd0ab43808a53058
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709759"
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="a7254-102">Nasıl yapılır: Test bir bölgeyle vuruş kullanma</span><span class="sxs-lookup"><span data-stu-id="a7254-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="a7254-103">İsabet sınaması amacı, imleci üzerine bir simge veya düğmesi gibi belirli bir nesne olup olmadığını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="a7254-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7254-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7254-104">Example</span></span>  
 <span data-ttu-id="a7254-105">Aşağıdaki örnek, iki dikdörtgen bölge birleşimi oluşturan tarafından artı şeklindeki bir bölge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7254-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="a7254-106">Varsayımında değişkeni `point` en son tıklayarak konumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a7254-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="a7254-107">Kod bakar olmadığını `point` artı şeklindeki bölgede.</span><span class="sxs-lookup"><span data-stu-id="a7254-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="a7254-108">(İsabet) bölgede noktasıysa bölge donuk bir kırmızı fırça ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a7254-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="a7254-109">Aksi takdirde, bölge, yarı saydam fırçalarla kırmızı fırça ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a7254-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7254-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a7254-110">Compiling the Code</span></span>  
 <span data-ttu-id="a7254-111">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="a7254-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7254-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7254-112">See also</span></span>
- <xref:System.Drawing.Region>
- [<span data-ttu-id="a7254-113">GDI+'daki Bölgeler</span><span class="sxs-lookup"><span data-stu-id="a7254-113">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="a7254-114">Nasıl yapılır: Bir bölgeyle kırpma kullanma</span><span class="sxs-lookup"><span data-stu-id="a7254-114">How to: Use Clipping with a Region</span></span>](how-to-use-clipping-with-a-region.md)
