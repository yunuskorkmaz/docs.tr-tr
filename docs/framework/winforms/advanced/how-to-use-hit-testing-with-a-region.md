---
title: "Nasıl yapılır: Bir Bölgeyle Vuruş Sınaması Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c0766c989df7c2329aa4d36af834378b02b1301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="15cdb-102">Nasıl yapılır: Bir Bölgeyle Vuruş Sınaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="15cdb-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="15cdb-103">İsabet testi amacı, imleç üzerinden bir simge veya düğmesi gibi belirli bir nesne olup olmadığını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="15cdb-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15cdb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="15cdb-104">Example</span></span>  
 <span data-ttu-id="15cdb-105">Aşağıdaki örnekte, iki dikdörtgen bölgeler birleşimi oluşturan tarafından artı şeklinde bir bölge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15cdb-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="15cdb-106">Varsayımında değişkeni `point` en son tıklatın konumunu tutar.</span><span class="sxs-lookup"><span data-stu-id="15cdb-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="15cdb-107">Kod bakar olup olmadığını `point` içinde artı şeklinde bölgedir.</span><span class="sxs-lookup"><span data-stu-id="15cdb-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="15cdb-108">Noktanın bölge (isabet) ise, bölge donuk kırmızı fırça ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="15cdb-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="15cdb-109">Aksi takdirde, bölge yarı saydam kırmızı fırça ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="15cdb-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15cdb-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="15cdb-110">Compiling the Code</span></span>  
 <span data-ttu-id="15cdb-111">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="15cdb-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15cdb-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15cdb-112">See Also</span></span>  
 <xref:System.Drawing.Region>  
 [<span data-ttu-id="15cdb-113">GDI+'daki Bölgeler</span><span class="sxs-lookup"><span data-stu-id="15cdb-113">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="15cdb-114">Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma</span><span class="sxs-lookup"><span data-stu-id="15cdb-114">How to: Use Clipping with a Region</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
