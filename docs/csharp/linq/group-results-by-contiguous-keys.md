---
title: Grup sonuçları bitişik anahtarlara göre
description: Nasıl Grup sonuçları bitişik anahtarlara göre yapılır.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 
