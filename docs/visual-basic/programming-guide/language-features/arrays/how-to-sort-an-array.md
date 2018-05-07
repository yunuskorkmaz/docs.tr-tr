---
title: "Nasıl yapılır: Visual Basic'de Bir Diziyi Sıralama"
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: a067c40e1dd0e881516cbc7769cb9afb879d1b9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Bir Diziyi Sıralama
Bu örnek, bir dizi bildirir `String` adlı nesneleri `zooAnimals`, bunu doldurduğundan ve alfabetik olarak sıralar.  
  
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
  
-   Mscorlib.dll erişimi ve <xref:System> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Dizi boşsa (<xref:System.ArgumentNullException> sınıfı)  
  
-   Dizi çok boyutlu (<xref:System.RankException> sınıfı)  
  
-   Dizinin bir veya daha fazla öğeleri uygulamaz <xref:System.IComparable> arabirimi (<xref:System.InvalidOperationException> sınıfı)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Koleksiyonlar](../../concepts/collections.md)  
 [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
