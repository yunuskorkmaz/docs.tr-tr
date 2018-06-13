---
title: For döngüsü denetim değişkeni olarak bildirilen dizi başlangıç boyutuyla bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: f6cf397b1e76313ab399d5e39a43ae0263df619c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587990"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>For döngüsü denetim değişkeni olarak bildirilen dizi başlangıç boyutuyla bildirilemez
A `For Each` döngü kullanan bir dizi olarak kendi *öğesi* yineleme değişkeni, ancak bu diziyi başlatır.  
  
 Aşağıdaki deyimleri nasıl bu hatayı oluşturulacağını gösterir.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 İlk `For Each` açıklamadır erişim öğeleri doğru şekilde `arrayList`. İkinci `For Each` deyimi bu hata oluşturur.  
  
 **Hata Kimliği:** BC32039  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Başlatma bildiriminden kaldırmak *öğesi* yineleme değişkeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Koleksiyonlar](../../../standard/collections/index.md)
