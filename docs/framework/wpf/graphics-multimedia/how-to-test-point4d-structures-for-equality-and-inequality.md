---
title: "Nasıl yapılır: Eşitlik ve Eşitsizlik için Point4D Yapılarını Test Etme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 849082fc1b933c4172c0d22ec3c9c2a1644a32fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="35b0b-102">Nasıl yapılır: Eşitlik ve Eşitsizlik için Point4D Yapılarını Test Etme</span><span class="sxs-lookup"><span data-stu-id="35b0b-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="35b0b-103">Bu örnek nasıl test edileceğini gösterir <xref:System.Windows.Media.Media3D.Point4D> yapıları için eşitlik ve eşitsizlik.</span><span class="sxs-lookup"><span data-stu-id="35b0b-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="35b0b-104">Aşağıdaki kodu nasıl test edileceğini gösterir <xref:System.Windows.Media.Media3D.Point4D> yapıları için eşitlik ve eşitsizlik kullanarak <xref:System.Windows.Media.Media3D.Point4D> eşitlik yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="35b0b-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="35b0b-105"><xref:System.Windows.Media.Media3D.Point4D> Yapıları aşırı yüklenmiş eşitlik kullanarak eşitlik için test (`==`) için daha sonra tekrar yüklenmiş eşitsizlik kullanılarak eşitsizlik işleci (`!=`) işleç ve son olarak bir <xref:System.Windows.Media.Media3D.Point3D> yapısı ve <xref:System.Windows.Media.Media3D.Point4D> Yapı statik kullanarak eşitlik için denetlenir <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35b0b-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35b0b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="35b0b-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="35b0b-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35b0b-107">See Also</span></span>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
