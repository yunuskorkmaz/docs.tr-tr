---
description: extern diğer adı-C# başvurusu
title: extern diğer adı-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 301ae06ec02fa6f09257dc87383bc2ec7f589b6d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139014"
---
# <a name="extern-alias-c-reference"></a>extern alias (C# Başvurusu)
Aynı tam tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir. Örneğin, bir derlemenin iki veya daha fazla sürümünü aynı uygulamada kullanmanız gerekebilir. Bir dış derleme diğer adı kullanarak, her derlemeden ad alanları, diğer ad tarafından adlandırılan ve aynı dosyada kullanılmasına olanak sağlayan kök düzeyi ad alanları içinde sarmalanabilir.  
  
> [!NOTE]
> [Extern](./extern.md) anahtar sözcüğü, yönetilmeyen kodda yazılmış bir yöntemi bildiren bir yöntem değiştiricisi olarak da kullanılır.  
  
 Aynı tam tür adlarıyla iki derlemeye başvurmak için, bir diğer ad aşağıdaki gibi bir komut isteminde belirtilmelidir:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Bu, dış diğer adları oluşturur `GridV1` ve `GridV2` . Bu diğer adları bir program içinden kullanmak için anahtar sözcüğünü kullanarak bunlara başvurun `extern` . Örneğin:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Her extern diğer ad bildirimi, genel ad alanını paraleller (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar. Bu nedenle, her bir derlemeden türler, uygun ad alanı-diğer adı altında belirtildiği gibi tam nitelikli adı kullanılarak belirsizlik olmadan başvuruda bulunulabilir.  
  
 Önceki örnekte, `GridV1::Grid` kılavuz denetimi olur `grid.dll` ve `GridV2::Grid` kılavuz denetimi olacaktır `grid20.dll` .  
  
## <a name="using-visual-studio"></a>Visual Studio’yu kullanma

Visual Studio kullanıyorsanız, diğer adlar benzer şekilde sağlanmış olabilir.

Visual Studio 'da projenize *grid.dll* ve *grid20.dll* başvurusu ekleyin. Bir özellik sekmesi açın ve Global olan diğer adları sırasıyla GridV1 ve GridV2 olarak değiştirin.

Bu diğer adları yukarıdaki şekilde kullanın

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

Artık *diğer ad yönergesini kullanarak*bir ad alanı veya tür için takma ad oluşturabilirsiniz. Daha fazla bilgi için bkz. [using yönergesi](using-directive.md).

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [:: İşleci](../operators/namespace-alias-qualifier.md)
- [-Reference (C# derleyici seçenekleri)](../compiler-options/reference-compiler-option.md)
