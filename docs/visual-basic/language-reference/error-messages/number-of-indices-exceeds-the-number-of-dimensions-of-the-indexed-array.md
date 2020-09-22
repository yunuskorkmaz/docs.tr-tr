---
title: Dizin sayısı, sıralı dizinin boyut sayısını aşıyor
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 3fc2744bb471eabd9345994b28fbef3ebc76f00d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873662"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>Dizin sayısı, sıralı dizinin boyut sayısını aşıyor

Bir dizi öğesine erişmek için kullanılan dizin sayısı, dizi sırasıyla tam olarak aynı olmalıdır, diğer bir deyişle, kendisi için belirtilen boyut sayısı.  
  
 **Hata kimliği:** BC30106  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Alt simgelerin toplam sayısı dizi derecesine eşit olana kadar alt simgeleri dizi başvurusundan kaldırın. Örnek:  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../programming-guide/language-features/arrays/index.md)
