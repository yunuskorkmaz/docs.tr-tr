---
description: 'Daha fazla bilgi edinin: nasıl yapılır: Visual Basic bir diziyi sıralama'
title: 'Nasıl yapılır: Dizi Sıralama'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: ea030b63dbbb5f5ea1d6160757afe2e9b58f7c21
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462769"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Nasıl yapılır: Visual Basic bir diziyi sıralama

Bu makalede, Visual Basic bir dize dizisinin nasıl sıralanacağını gösteren bir örnek gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnek `String` , adlı bir nesne dizisi bildirir `zooAnimals` , onu doldurur ve alfabetik olarak sıralar:
  
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

- Dizi boş ( <xref:System.ArgumentNullException> sınıf).
- Dizi çok boyutlu ( <xref:System.RankException> sınıf).
- Dizinin bir veya daha fazla öğesi <xref:System.IComparable> arabirimini uygulamıyor ( <xref:System.InvalidOperationException> sınıf).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Diziler](index.md)
- [Dizilerle İlgili Sorun Giderme](troubleshooting-arrays.md)
- [Koleksiyonlar](../../concepts/collections.md)
- [For Each...Next Deyimi](../../../language-reference/statements/for-each-next-statement.md)
