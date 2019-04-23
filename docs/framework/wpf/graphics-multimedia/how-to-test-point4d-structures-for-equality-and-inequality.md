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
ms.openlocfilehash: ce1188e99ef2b0682427cc2e227aaccd27f7c4f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770158"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>Nasıl yapılır: Eşitlik ve Eşitsizlik için Point4D Yapılarını Test Etme
Bu örnek nasıl test edileceğini gösterir <xref:System.Windows.Media.Media3D.Point4D> yapıları eşitlik ve eşitsizlik için.  
  
 Aşağıdaki kod nasıl test edileceğini göstermektedir <xref:System.Windows.Media.Media3D.Point4D> yapıları için eşitlik ve eşitsizlik kullanarak <xref:System.Windows.Media.Media3D.Point4D> eşitlik yöntemleri.  <xref:System.Windows.Media.Media3D.Point4D> Yapıları aşırı yüklenmiş eşitlik kullanarak eşitlik için test (`==`) işleci, aşırı yüklenmiş eşitsizlik kullanarak ardından eşitsizlik için (`!=`) işleç ve son olarak bir <xref:System.Windows.Media.Media3D.Point3D> yapısı ve <xref:System.Windows.Media.Media3D.Point4D> yapısı, statik kullanarak eşitlik için denetlenir <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
