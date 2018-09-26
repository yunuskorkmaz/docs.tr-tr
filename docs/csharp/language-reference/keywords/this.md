---
title: this (C# Başvurusu)
description: Bu anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: df1bf6a3e6d24b231bf5e3c7a960f49084c4e53a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209392"
---
# <a name="this-c-reference"></a>this (C# Başvurusu)
`this` Anahtar sözcüğü sınıfın geçerli örneğine başvurur ve genişletme yönteminin ilk parametresinin bir değiştirici da kullanılır.  
  
> [!NOTE]
>  Bu makalede kullanımı ele alınmaktadır `this` sınıf örneğine sahip. Kullanımını genişletme yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 ' In yaygın kullanımları şunlardır `this`:  
  
-   Örneğin benzer adlarla gizli üyeleri nitelemek için:  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Diğer yöntemleri için parametre olarak nesne örneğin iletmek için:  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   Dizin Oluşturucular, örneğin bildirmek için:  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Bir nesnenin parçası olarak değil de sınıf düzeyinde olduğundan statik üye işlevleri yoktur bir `this` işaretçi. Başvurmak için bir hata olduğunu `this` statik yöntemde.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `this` nitelemek için kullanılan `Employee` sınıf üyeleri, `name` ve `alias`, benzer adlarla gizlidir. Bir nesne yönteme geçirmek için de kullanılır `CalcTax`, başka bir sınıfa aittir.  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [base](../../../csharp/language-reference/keywords/base.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
