---
title: "Nasıl yapılır: 3B Görünümü Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd84a95bf793b3da9970b605b2f02509e3938ab0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-3-d-scene"></a><span data-ttu-id="02c1e-102">Nasıl yapılır: 3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02c1e-102">How to: Create a 3-D Scene</span></span>
<span data-ttu-id="02c1e-103">Bu örnek düz bir yaprak Döndürülmüş kağıt gibi görünen 3-b bir nesnesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02c1e-103">This example shows how to create a 3-D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="02c1e-104">A <xref:System.Windows.Controls.Viewport3D> aşağıdaki bileşenleri ile birlikte bu basit 3B görünümü oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="02c1e-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3-D scene:</span></span>  
  
-   <span data-ttu-id="02c1e-105">Kamera kullanılarak oluşturulan bir <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="02c1e-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="02c1e-106">Kamera 3B Sahne hangi kısmının görüntülenebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02c1e-106">The camera specifies what part of the 3-D scene is viewable.</span></span>  
  
-   <span data-ttu-id="02c1e-107">Şekil 3-b nesnenin (yaprak kağıt) kullanarak belirtmek için bir kafes oluşturulur <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="02c1e-107">A mesh is created to specify the shape of 3-D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="02c1e-108">Bir malzeme nesnesi (Bu örnekte doğrusal gradyan) kullanılarak yüzey üzerinde görüntülenecek belirtilen <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="02c1e-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="02c1e-109">Bir açık kullanarak nesne üzerinde görünmek için oluşturulan <xref:System.Windows.Media.Media3D.DirectionalLight>.</span><span class="sxs-lookup"><span data-stu-id="02c1e-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02c1e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="02c1e-110">Example</span></span>  
 <span data-ttu-id="02c1e-111">Aşağıdaki kodu XAML'de 3B Sahne oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02c1e-111">The code below shows how to create a 3-D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="02c1e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="02c1e-112">Example</span></span>  
 <span data-ttu-id="02c1e-113">Aşağıdaki kodu yordam kodda aynı 3B Sahne oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02c1e-113">The code below shows how to create the same 3-D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="02c1e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02c1e-114">See Also</span></span>  
 [<span data-ttu-id="02c1e-115">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="02c1e-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
