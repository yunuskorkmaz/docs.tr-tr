---
title: Anonim türdeki üye adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: 4d91b7a3c57db38fde3cf371773e8d64834a8f72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715276"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Anonim türdeki üye adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan gösterilebilir
Bir anonim türdeki üye adı karmaşık bir ifadeden çıkarsanamaz.  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 Anonim türler içinden olabilir ve üye adlarını ve türlerini çıkarsanamıyor kaynakları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
 **Hata Kimliği:** BC36556  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İfade, aşağıdaki kodda gösterildiği gibi bir üye adına atayın:  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
