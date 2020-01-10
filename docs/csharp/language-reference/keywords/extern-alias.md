---
title: extern diğer ad C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713541"
---
# <a name="extern-alias-c-reference"></a>extern alias (C# Başvurusu)
Aynı tam tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir. Örneğin, bir derlemenin iki veya daha fazla sürümünü aynı uygulamada kullanmanız gerekebilir. Bir dış derleme diğer adı kullanarak, her derlemeden ad alanları, diğer ad tarafından adlandırılan ve aynı dosyada kullanılmasına olanak sağlayan kök düzeyi ad alanları içinde sarmalanabilir.  
  
> [!NOTE]
> [Extern](./extern.md) anahtar sözcüğü, yönetilmeyen kodda yazılmış bir yöntemi bildiren bir yöntem değiştiricisi olarak da kullanılır.  
  
 Aynı tam tür adlarıyla iki derlemeye başvurmak için, bir diğer ad aşağıdaki gibi bir komut isteminde belirtilmelidir:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Bu, `GridV1` ve `GridV2`dış diğer adlarını oluşturur. Bu diğer adları bir program içinden kullanmak için, `extern` anahtar sözcüğünü kullanarak bunlara başvurun. Örneğin:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Her extern diğer ad bildirimi, genel ad alanını paraleller (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar. Bu nedenle, her bir derlemeden türler, uygun ad alanı-diğer adı altında belirtildiği gibi tam nitelikli adı kullanılarak belirsizlik olmadan başvuruda bulunulabilir.  
  
 Önceki örnekte, `GridV1::Grid` kılavuz denetimi `grid.dll`ve `grid20.dll``GridV2::Grid` kılavuz denetimi olacaktır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [:: İşleci](../operators/namespace-alias-qualifier.md)
- [-Reference (C# derleyici seçenekleri)](../compiler-options/reference-compiler-option.md)
