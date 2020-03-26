---
title: Nasıl? 3B Modelin Ölçeğini Dönüştürün
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111991"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a><span data-ttu-id="d2dba-102">Nasıl? 3B Modelin Ölçeğini Dönüştürün</span><span class="sxs-lookup"><span data-stu-id="d2dba-102">How to: Transform the Scale of a 3D Model</span></span>
<span data-ttu-id="d2dba-103">Bu örnek, 3B nesnenin nasıl ölçeklendirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2dba-103">This example shows how to scale a 3D object.</span></span> <span data-ttu-id="d2dba-104">Bir 3B nesneyi ölçeklendirmek için bir <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="d2dba-104">To scale a 3D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="d2dba-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> ve özellikleri belirttiğiniz faktöre göre öğeyi yeniden boyutlandırmak.</span><span class="sxs-lookup"><span data-stu-id="d2dba-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="d2dba-106">Örneğin, 1,5 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> değeri bir nesneyi özgün genişliğinin yüzde 150'sine kadar uzatür.</span><span class="sxs-lookup"><span data-stu-id="d2dba-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="d2dba-107">0,5 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> değeri bir nesnenin yüksekliğini yüzde 50 küçültür.</span><span class="sxs-lookup"><span data-stu-id="d2dba-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="d2dba-108">Aşağıdaki kod, bir <xref:System.Windows.Media.Media3D.ScaleTransform3D> <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="d2dba-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="d2dba-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2dba-109">Example</span></span>  
 <span data-ttu-id="d2dba-110">Aşağıdaki kod, tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2dba-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d2dba-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2dba-111">See also</span></span>

- [<span data-ttu-id="d2dba-112">Animasyon 3D Çeviriler</span><span class="sxs-lookup"><span data-stu-id="d2dba-112">Animate 3D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="d2dba-113">3B Sahne Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2dba-113">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d2dba-114">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d2dba-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
