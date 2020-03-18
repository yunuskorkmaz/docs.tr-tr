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
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160371"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Ortak dil çalışma zamanında tür iletme
Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.  
  
 Örneğin, bir `Example` *uygulamanın Utility.dll*adlı bir derlemede sınıfı kullandığını varsayalım. *Utility.dll* geliştiricileri derlemeyi yeniden düzenlemeye karar verebilir ve bu `Example` süreçte sınıfı başka bir derlemeye taşıyabilirler. *Utility.dll'nin* eski sürümü *Utility.dll'nin* yeni sürümü ve yardımcı derlemesi ile `Example` değiştirilirse, sınıfı `Example` kullanan *uygulama, Utility.dll'nin*yeni sürümünde sınıfı bulamadığı için başarısız olur.  
  
 *Utility.dll* geliştiricileri özniteliği `Example` kullanarak, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> sınıf için istekleri ileterek bunu önleyebilirsiniz. Öznitelik *Utility.dll'nin*yeni sürümüne uygulandıysa, `Example` sınıf istekleri şimdi sınıfı içeren derlemeye iletilir. Varolan uygulama, derleme olmadan normal şekilde çalışmaya devam eder.  
  
> [!NOTE]
> .NET Framework sürüm 2.0'da, Visual Basic'te yazılmış derlemelerden türleri iledemezsiniz. Ancak, Visual Basic'te yazılmış bir uygulama iletilen türleri tüketebilir. Diğer bir deyişle, uygulama C# veya C++'da kodlanmış bir derleme kullanıyorsa ve bu derlemeden bir tür başka bir derlemeye iletilirse, Visual Basic uygulaması iletilen türü kullanabilir.  
  
## <a name="forward-types"></a>İleri türleri  
 Bir türü iletmek için dört adım vardır:  
  
1. Türüiçin kaynak kodunu özgün derlemeden hedef derlemeye taşıyın.  

2. Türün bulunduğu derlemede, taşınan tür için <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> bir ekleyin. Aşağıdaki kod, taşınan bir `Example` tür için özniteliği gösterir.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Şimdi türü içeren derlemeyi derle.  

4. Şimdi türü içeren derlemebir başvuru ile, tür eskiden bulunan derleme yeniden derle. Örneğin, komut satırından bir C# dosyası derliyorsanız, türü içeren derlemeyi belirtmek için [-başvuru (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın. C++'da, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Tip yönlendirme (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using yönergesi](/cpp/preprocessor/hash-using-directive-cpp)
