---
title: Nasıl?
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112108"
---
# <a name="how-to-create-a-3d-scene"></a><span data-ttu-id="63d5c-102">Nasıl?</span><span class="sxs-lookup"><span data-stu-id="63d5c-102">How to: Create a 3D Scene</span></span>
<span data-ttu-id="63d5c-103">Bu örnek, döndürülmüş düz bir kağıt sayfasına benzeyen bir 3B nesnenin nasıl oluşturulutamamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63d5c-103">This example shows how to create a 3D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="63d5c-104">Bu <xref:System.Windows.Controls.Viewport3D> basit 3B sahneyi oluşturmak için aşağıdaki bileşenlerle birlikte kullanılır:</span><span class="sxs-lookup"><span data-stu-id="63d5c-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3D scene:</span></span>  
  
- <span data-ttu-id="63d5c-105">Bir kamera kullanılarak <xref:System.Windows.Media.Media3D.PerspectiveCamera>oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63d5c-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="63d5c-106">Kamera, 3B sahnenin hangi bölümünün görüntülenebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="63d5c-106">The camera specifies what part of the 3D scene is viewable.</span></span>  
  
- <span data-ttu-id="63d5c-107">3B nesnenin (kağıt sayfası) <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> şeklini belirtmek için bir kafes <xref:System.Windows.Media.Media3D.GeometryModel3D>oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63d5c-107">A mesh is created to specify the shape of 3D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="63d5c-108">Bir malzeme nesnenin yüzeyinde görüntülenecek belirtilir (bu örnekte doğrusal <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> degrade) özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>kullanılarak.</span><span class="sxs-lookup"><span data-stu-id="63d5c-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="63d5c-109">Bir ışık kullanarak <xref:System.Windows.Media.Media3D.DirectionalLight>nesne üzerinde parlamak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63d5c-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63d5c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="63d5c-110">Example</span></span>  
 <span data-ttu-id="63d5c-111">Aşağıdaki kod, XAML'de nasıl bir 3B sahne oluşturulacak gösteriş gösterir.</span><span class="sxs-lookup"><span data-stu-id="63d5c-111">The code below shows how to create a 3D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="63d5c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="63d5c-112">Example</span></span>  
 <span data-ttu-id="63d5c-113">Aşağıdaki kod, yordam kodunda aynı 3B sahnenin nasıl oluşturuleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="63d5c-113">The code below shows how to create the same 3D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="63d5c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63d5c-114">See also</span></span>

- [<span data-ttu-id="63d5c-115">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="63d5c-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
