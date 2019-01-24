---
title: extern diğer adı - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 136d3959a52b793acddf21ae83b8d8eaec053eee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616283"
---
# <a name="extern-alias-c-reference"></a>extern alias (C# Başvurusu)
İki sürümünü tam olarak nitelenmiş tür adları aynı bütünleştirilmiş kodları başvuru yapması gerekli olabilir. Örneğin, aynı uygulamada iki veya daha fazla derleme sürümünü kullanmanız gerekebilir. Bir dış bütünleştirilmiş diğer adı kullanarak, aynı dosyada kullanılmak üzere etkinleştirir diğer ad tarafından adlandırılan kök düzeyinde ad alanları içinde her derlemenin ad alanlarını sarmalanabilir.  
  
> [!NOTE]
>  [Extern](../../../csharp/language-reference/keywords/extern.md) anahtar sözcüğü yönetilmeyen kodda yazılmış bir yöntemi bildirmek, bir yöntemi değiştirici olarak da kullanılır.  
  
 İki derlemenin aynı tam olarak nitelenmiş tür adları ile başvurmak için bir diğer ad bir komut isteminde şu şekilde belirtilmelidir:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Bu dış diğer oluşturur `GridV1` ve `GridV2`. Bir programın gelen bu diğer adlar kullanmak için bunları kullanarak başvuru `extern` anahtar sözcüğü. Örneğin:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Parallels (ancak içinde yer almıyor) bir ek kök düzeyinde ad alanı her extern diğer ad bildirimi tanıtır genel ad. Bu nedenle her derlemesinden türleri için belirsizlik kökü uygun namespace-diğer kullanıcıların tam adı, kullanarak bulunulabilir.  
  
 Önceki örnekte, `GridV1::Grid` kılavuz denetiminden olacaktır `grid.dll`, ve `GridV2::Grid` kılavuz denetiminden olacaktır `grid20.dll`.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [:: İşleç](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [/ Reference (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
