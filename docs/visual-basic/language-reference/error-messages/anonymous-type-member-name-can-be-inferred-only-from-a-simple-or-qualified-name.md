---
title: Anonim türdeki üye adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: f4f62a9ac97c6dbd8d2426f8bfd17afa66c4001a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587475"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="a6a93-102">Anonim türdeki üye adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan gösterilebilir</span><span class="sxs-lookup"><span data-stu-id="a6a93-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="a6a93-103">Bir anonim türdeki üye adı karmaşık ifadesinden gösterilemiyor.</span><span class="sxs-lookup"><span data-stu-id="a6a93-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="a6a93-104">Anonim türler içinden olabilir ve üye adlarını ve türlerini gösterilemez kaynakları hakkında daha fazla bilgi için bkz: [nasıl yapılır: Infer özellik adları ve türlerini anonim türde bildirimlerden](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="a6a93-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="a6a93-105">**Hata Kimliği:** BC36556</span><span class="sxs-lookup"><span data-stu-id="a6a93-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6a93-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a6a93-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a6a93-107">İfade üye adı için aşağıdaki kodda gösterildiği gibi atayın:</span><span class="sxs-lookup"><span data-stu-id="a6a93-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a6a93-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6a93-108">See Also</span></span>  
 [<span data-ttu-id="a6a93-109">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="a6a93-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="a6a93-110">Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma</span><span class="sxs-lookup"><span data-stu-id="a6a93-110">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
