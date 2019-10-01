---
title: "Nasıl yapılır: Visual Basic'de Bir Diziyi Sıralama"
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700972"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Nasıl yapılır: Visual Basic bir diziyi sıralama

Bu makalede, Visual Basic bir dize dizisinin nasıl sıralanacağını gösteren bir örnek gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnek, `zooAnimals` adlı `String` nesnelerinin bir dizisini bildirir, onu doldurur ve alfabetik olarak sıralar:
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a>Güçlü programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Dizi boş (<xref:System.ArgumentNullException> sınıfı).
- Dizi çok boyutlu (<xref:System.RankException> sınıfı).
- Dizinin bir veya daha fazla öğesi <xref:System.IComparable> arabirimini uygulamıyor (<xref:System.InvalidOperationException> sınıfı).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Diziler](index.md)
- [Dizilerle İlgili Sorun Giderme](troubleshooting-arrays.md)
- [Koleksiyonlar](../../concepts/collections.md)
- [For Each...Next Deyimi](../../../language-reference/statements/for-each-next-statement.md)
