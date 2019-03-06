---
title: 'Nasıl yapılır: Eşitlik ve Eşitsizlik için Point4D Yapılarını Test Etme'
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: d72aef8a1328742f0b04c2ad009126e21390398a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367212"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="b6d39-102">Nasıl yapılır: Eşitlik ve Eşitsizlik için Point4D Yapılarını Test Etme</span><span class="sxs-lookup"><span data-stu-id="b6d39-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="b6d39-103">Bu örnek nasıl test edileceğini gösterir <xref:System.Windows.Media.Media3D.Point4D> yapıları eşitlik ve eşitsizlik için.</span><span class="sxs-lookup"><span data-stu-id="b6d39-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="b6d39-104">Aşağıdaki kod nasıl test edileceğini göstermektedir <xref:System.Windows.Media.Media3D.Point4D> yapıları için eşitlik ve eşitsizlik kullanarak <xref:System.Windows.Media.Media3D.Point4D> eşitlik yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b6d39-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="b6d39-105"><xref:System.Windows.Media.Media3D.Point4D> Yapıları aşırı yüklenmiş eşitlik kullanarak eşitlik için test (`==`) işleci, aşırı yüklenmiş eşitsizlik kullanarak ardından eşitsizlik için (`!=`) işleç ve son olarak bir <xref:System.Windows.Media.Media3D.Point3D> yapısı ve <xref:System.Windows.Media.Media3D.Point4D> yapısı, statik kullanarak eşitlik için denetlenir <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b6d39-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6d39-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6d39-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="b6d39-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6d39-107">See also</span></span>
- <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
