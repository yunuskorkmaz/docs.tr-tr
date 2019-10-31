---
title: Ortak dil çalışma zamanında tür iletme
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 7b9fd4e89d1d3290dfc17f52de392c4ee9092d02
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138592"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Ortak dil çalışma zamanında tür iletme
Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.  
  
 Örneğin, bir uygulamanın *Utility. dll*adlı bir derlemede `Example` sınıfını kullandığını varsayalım. *Utility. dll* ' nin geliştiricileri derlemeyi yeniden düzenleme kararı verebilir ve süreçte `Example` sınıfını başka bir derlemeye taşıyabilirler. *Utility. dll* ' nin eski sürümü *Utility. dll* ' nin yeni sürümü ve yardımcı bütünleştirilmiş kodu tarafından değiştirilirse, `Example` sınıfını kullanan uygulama, *yardımcı program. dll* ' nin yeni sürümünde `Example` sınıfını bulamadığından başarısız olur. .  
  
 *Utility. dll* ' nin geliştiricileri, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> özniteliğini kullanarak `Example` sınıfı için istekleri ileterek bundan kaçınabilir. Özniteliği, *Utility. dll*' nin yeni sürümüne uygulanmışsa, `Example` sınıfına yönelik istekler, artık sınıfı içeren derlemeye iletilir. Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' de, Visual Basic yazılmış derlemelerden türleri iletemezsiniz. Ancak, Visual Basic yazılmış bir uygulama iletilen türleri kullanabilir. Yani, uygulama veya C# C++içinde kodlanmış bir derlemeyi kullanıyorsa ve bu derlemedeki bir tür başka bir derlemeye iletilirse, Visual Basic uygulama iletilen türü kullanabilir.  
  
## <a name="forward-types"></a>İleri türleri  
 Bir türü iletmek için dört adım vardır:  
  
1. Asıl derlemeden hedef derlemeye tür için kaynak kodunu taşıyın.  
   
2. Türün bulunması için kullanıldığı derlemede, taşınan tür için bir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> ekleyin. Aşağıdaki kod, taşınan `Example` adlı bir tür için özniteliğini gösterir.  
   
   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```
   
   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  
   
3. Artık türü içeren derlemeyi derleyin.  
   
4. Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin. Örneğin, komut satırından bir C# dosya derlerken, türü içeren derlemeyi belirtmek için [-Reference (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın. İçinde C++, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Tür iletme (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using yönergesi](/cpp/preprocessor/hash-using-directive-cpp)
