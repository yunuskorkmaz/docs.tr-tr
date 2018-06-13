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
ms.openlocfilehash: 1ec844c8fb0aceaaec6030c2e9d5cb30cf984f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559820"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>Nasıl yapılır: Eşitlik ve Eşitsizlik için Point4D Yapılarını Test Etme
Bu örnek nasıl test edileceğini gösterir <xref:System.Windows.Media.Media3D.Point4D> yapıları için eşitlik ve eşitsizlik.  
  
 Aşağıdaki kodu nasıl test edileceğini gösterir <xref:System.Windows.Media.Media3D.Point4D> yapıları için eşitlik ve eşitsizlik kullanarak <xref:System.Windows.Media.Media3D.Point4D> eşitlik yöntemleri.  <xref:System.Windows.Media.Media3D.Point4D> Yapıları aşırı yüklenmiş eşitlik kullanarak eşitlik için test (`==`) için daha sonra tekrar yüklenmiş eşitsizlik kullanılarak eşitsizlik işleci (`!=`) işleç ve son olarak bir <xref:System.Windows.Media.Media3D.Point3D> yapısı ve <xref:System.Windows.Media.Media3D.Point4D> Yapı statik kullanarak eşitlik için denetlenir <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
