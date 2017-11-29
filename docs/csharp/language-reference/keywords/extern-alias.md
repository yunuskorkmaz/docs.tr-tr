---
title: "extern alias (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e995586c08659853538726a12679770cd1ada37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extern-alias-c-reference"></a>extern alias (C# Başvurusu)
Aynı tam olarak nitelenmiş tür adları olan derlemeler iki sürümü başvuru gerekebilir. Örneğin, bir derlemeyi iki veya daha fazla sürümünü ve aynı uygulamada kullanmanız gerekebilir. Bir dış derleme diğer adı kullanarak, ad alanlarının her derlemesinden bunları aynı dosyada kullanılacak sağlayan diğer adı tarafından adlı kök düzeyinde ad içinde sarmalamak.  
  
> [!NOTE]
>  [Extern](../../../csharp/language-reference/keywords/extern.md) anahtar sözcüğü yönetilmeyen kod içinde yazılmış bir yöntem bildirme bir yöntemi değiştirici olarak da kullanılır.  
  
 İki derlemeleri aynı tam olarak nitelenmiş tür adları ile başvurmak için bir diğer ad bir komut isteminde şu şekilde belirtilmelidir:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Bu dış diğer adlar oluşturur `GridV1` ve `GridV2`. Bir programdan gelen bu diğer adları kullanmak için bunları kullanarak başvuru `extern` anahtar sözcüğü. Örneğin:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Parallels (ancak içinde bulunmayacak) bir ek kök düzeyinde ad alanı her extern alias bildirimi tanıtır genel ad alanı. Bu nedenle her derleme türlerinden için karışıklık uygun ad alanı-diğer kökü kullanıcıların tam adı, kullanılarak belirtilebilir.  
  
 Önceki örnekte, `GridV1::Grid` kılavuz denetiminden olacaktır `grid.dll`, ve `GridV2::Grid` kılavuz denetiminden olacaktır `grid20.dll`.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [:: İşleci](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [/ Reference (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
