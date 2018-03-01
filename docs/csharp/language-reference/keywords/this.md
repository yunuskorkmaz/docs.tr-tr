---
title: "this (C# Başvurusu)"
description: "Bu anahtar sözcüğü (C# Başvurusu)"
keywords: "Bu (C#), bu anahtar sözcüğü (C#), bu anahtar sözcüğü (C# Başvurusu), bu anahtar sözcüğü (C# dili Başvurusu)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a>this (C# Başvurusu)
`this` Anahtar sözcüğü sınıfının geçerli örneği başvuruyor ve bir ilk parametresi bir genişletme yöntemi değiştirici da kullanılır.  
  
> [!NOTE]
>  Bu makalede kullanımını ele `this` sınıf örnekleri ile. Kullanımını genişletme yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 ' In yaygın kullanımları şunlardır `this`:  
  
-   Benzer adları, örneğin gizli üyeleri nitelemek için:  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Örneğin diğer yöntemleri için bir nesne bir parametre olarak geçirmek için:  
  
    ```  
    CalcTax(this);  
    ```  
  
-   Dizin Oluşturucular, örneğin bildirmek için:  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Statik üye işlevleri, bir nesnenin parçası olarak değil de sınıf düzeyinde olmadıklarından sahip bir `this` işaretçi. Başvurmak için bir hata olduğunu `this` bir statik yöntem.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `this` nitelemek için kullanılan `Employee` sınıfı üyelerine, `name` ve `alias`, benzer adlarıyla gizlidir. Bir nesne yönteme de kullanılan `CalcTax`, başka bir sınıfa ait olduğu.  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [temel](../../../csharp/language-reference/keywords/base.md)  
 [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)
