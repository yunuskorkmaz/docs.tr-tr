---
title: extern takma adı - C# Başvurusu
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713541"
---
# <a name="extern-alias-c-reference"></a>extern alias (C# Başvurusu)
Aynı tam nitelikli tür adlarına sahip derlemelerin iki sürümüne başvurmanız gerekebilir. Örneğin, aynı uygulamada bir derlemenin iki veya daha fazla sürümü kullanmanız gerekebilir. Dış derleme takma adı kullanılarak, her derlemedeki ad boşlukları, diğer adla adlandırılan kök düzeyindead boşluklarıiçinde paketlenebilir ve bu da aynı dosyada kullanılmasını sağlar.  
  
> [!NOTE]
> [Extern](./extern.md) anahtar sözcüğü, yönetilmeyen kodla yazılmış bir yöntem bildiren bir yöntem değiştirici olarak da kullanılır.  
  
 Aynı tam nitelikli tür adlarına sahip iki derlemeye başvurmak için, bir diğer adın komut isteminde aşağıdaki gibi belirtilmesi gerekir:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Bu dış takma adlar `GridV1` `GridV2`oluşturur ve. Bu diğer adları bir program içinden kullanmak için, anahtar sözcüğü kullanarak bunlara başvurun. `extern` Örnek:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Her extern diğer ad bildirimi, genel ad alanına paralel (ancak içinde olmayan) ek bir kök düzeyi ad alanı sunar. Böylece, her derlemeden gelen türler, uygun ad alanı-diğer adlarına dayanan tam nitelikli adlarını kullanarak belirsizlik olmadan başvurulabilir.  
  
 Önceki örnekte, `GridV1::Grid` 'den `grid.dll`ızgara denetimi `GridV2::Grid` olacaktır ve `grid20.dll`.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [:: Operatör](../operators/namespace-alias-qualifier.md)
- [-referans (C# Derleyici Seçenekleri)](../compiler-options/reference-compiler-option.md)
