---
title: 'Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 22d2cf788d4726488512703356a75f84efd04250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278512"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama
Aşağıdaki örnek, statik bölümlendirme gerçekleştiren PLıNQ için basit bir özel bölümleyici uygulamak için bir yol gösterir. Bölümleyici dinamik bölümleri desteklemediğinden, bu, ' den tüketilemez değildir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . Bu belirli bir bölümleyici, her öğenin artan miktarda işleme süresi gerektirdiği veri kaynakları için varsayılan Aralık bölümleyici 'nin üzerinde iyileşme sağlayabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Bu örnekteki bölümler her öğe için işleme zamanında doğrusal bir artışın varsayımına dayanır. Gerçek dünyada, işleme sürelerini bu şekilde tahmin etmek zor olabilir. Belirli bir veri kaynağıyla statik bir bölümleyici kullanıyorsanız, kaynağın bölümlendirme formülünü iyileştirebilir, Yük Dengeleme mantığını ekleyebilir veya [nasıl yapılır: dinamik bölümleri uygulama](how-to-implement-dynamic-partitions.md)bölümünde gösterildiği gibi öbek bölümleme yaklaşımını kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [PLıNQ ve TPL için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md)
