---
title: "Nasıl yapılır: Visual Basic'de Bir Diziyi Sıralama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f24c0625058dbd960411d5981b4e98e0e9422b99
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
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
