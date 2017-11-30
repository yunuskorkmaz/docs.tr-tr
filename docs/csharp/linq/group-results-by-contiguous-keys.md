---
title: "Grup sonuçları bitişik anahtarlara göre"
description: "Nasıl Grup sonuçları bitişik anahtarlara göre yapılır."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: cdd06a6fad037291bbc5aa011b47bb668fa2f062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="group-results-by-contiguous-keys"></a>Grup sonuçları bitişik anahtarlara göre

Aşağıdaki örnek, bitişik anahtarlara sıraları temsil eden parçalara öğeleri gruplandırmak gösterilmiştir. Örneğin, aşağıdaki anahtar-değer çiftleri dizisi verildiğini varsayın:  
  
|Anahtar|Değer|  
|---------|-----------|  
|BİR|Biz|  
|BİR|Düşünme|  
|BİR|,|  
|B|LINQ|  
|C|is|  
|BİR|gerçekten|  
|B|Seyrek erişimli|  
|B|!|  
  
 Bu sırada aşağıdaki grupları oluşturulur:  
  
1.  Düşünüyoruz,  
  
2.  LINQ  
  
3.  is  
  
4.  gerçekten  
  
5.  Cool!  
  
 Çözüm, iş parçacığı açısından güvenli olan ve bir akış şekilde sonuçları döndüren bir genişletme yöntemi olarak uygulanır. Diğer bir deyişle, kaynak sırası hareket ederken, grupları oluşturur. Farklı `group` veya `orderby` operatörleri onu başlayabilir çağırana grupları döndüren dizisi tümüne okumadan önce.  
  
 İş parçacığı güvenliği kaynak sıradaki yinelendiğinde gibi her bir grup veya öbek bir kopyasını kaynak kodu açıklamaları açıklandığı gibi sağlayarak gerçekleştirilir. Kaynak sırası büyük dizi bitişik öğesi içeriyorsa, ortak dil çalışma zamanı atabilir bir <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genişletme yöntemi ve onu kullanan istemci kodu gösterir.  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 Projenizde genişletme yöntemi kullanmak için kopyalayın `MyExtensions` yeni veya var olan bir kaynak için statik sınıf kod dosyası ve gerekli ise ekleyin bir `using` bulunduğu olduğu ad alanı için yönerge.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)  
 
