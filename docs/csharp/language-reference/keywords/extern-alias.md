---
title: extern alias (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: a2803d09ee64af854cad352f6a158fb84bb6d410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217395"
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [:: İşleci](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [/ Reference (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
