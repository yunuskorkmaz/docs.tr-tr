---
title: Sonuçları bitişik tuşlara göre gruplandırma (C#'da LINQ)
description: C#'da LINQ kullanarak bitişik tuşlarla sonuçları nasıl gruplandırmak.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659910"
---
# <a name="group-results-by-contiguous-keys"></a>Sonuçları bitişik anahtarlara göre gruplama

Aşağıdaki örnek, öğeleri bitişik anahtarların alt dizilerini temsil eden parçalar halinde nasıl gruplanır gösterilmektedir. Örneğin, size aşağıdaki anahtar değeri çiftleri sırasının verildiğini varsayalım:

|Anahtar|Değer|
|---------|-----------|
|A|Biz|
|A|Düşünü|
|A|bu|
|B|Lınq|
|C|is|
|A|Gerçek -ten|
|B|Serin|
|B|!|

Aşağıdaki gruplar bu sırada oluşturulur:

1. Biz, düşünüyorum, bu

2. Lınq

3. is

4. Gerçek -ten

5. Serin!

Çözüm, iş parçacığı güvenli ve sonuçlarını akışlı bir şekilde döndüren bir uzantı yöntemi olarak uygulanır. Başka bir deyişle, kaynak sırayla hareket ederken gruplarını üretir. Veya `group` `orderby` işleçlerin aksine, tüm sıra okunmadan önce grupları arayanın anına döndürmeye başlayabilir.

Konu güvenliği, kaynak kod yorumlarında açıklandığı gibi, kaynak sırası yinelenirken her grubun veya yığının bir kopyasını oluşturarak gerçekleştirilir. Kaynak sıranın büyük bir bitişik öğe sırası varsa, ortak dil <xref:System.OutOfMemoryException>çalışma süresi bir .

## <a name="example"></a>Örnek

Aşağıdaki örnek, hem uzantı yöntemini hem de onu kullanan istemci kodunu gösterir:

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

Projenizdeki uzantı yöntemini kullanmak `MyExtensions` için statik sınıfı yeni veya varolan kaynak kodu dosyasına kopyalayın ve gerekirse bulunduğu ad alanı için bir `using` yönerge ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
