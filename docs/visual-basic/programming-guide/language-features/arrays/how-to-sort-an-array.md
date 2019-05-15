---
title: "Nasıl yapılır: Visual Basic'te dizi Sırala"
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 680f488a98d6e7e31b3d077843514fd12f75481c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586436"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te dizi Sırala
Bu örnek, bir dizi bildirir `String` adlı nesneleri `zooAnimals`, onu doldurur ve alfabetik olarak sıralar.  
  
## <a name="example"></a>Örnek  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Erişim <xref:System> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dizi boş (<xref:System.ArgumentNullException> sınıfı)  
  
- Dizi çok boyutlu (<xref:System.RankException> sınıfı)  
  
- Bir veya daha fazla öğe dizinin uygulamayın <xref:System.IComparable> arabirimi (<xref:System.InvalidOperationException> sınıfı)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Koleksiyonlar](../../concepts/collections.md)
- [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
