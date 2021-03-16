---
title: Ortak dil çalışma zamanında tür iletme
description: Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir .NET derlemesine taşımanızı sağlar.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 000abb5846d3ccfc1f422b8a70c4d8573d08de46
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479358"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Ortak dil çalışma zamanında tür iletme

Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.  
  
 Örneğin, bir uygulamanın `Example` sınıfı *Utility.dll* adlı bir derlemede kullandığını varsayalım. *Utility.dll* geliştiricileri derlemeyi yeniden düzenleme kararı verebilir ve süreçte `Example` sınıfı başka bir derlemeye taşıyabilir. *Utility.dll* eski sürümü *Utility.dll* yeni sürümü ve yardımcı bütünleştirilmiş kodu ile değiştirilirse, sınıfı kullanan uygulama, `Example` `Example` sınıfı yeni *Utility.dll* sürümünde konumlandıramadığından başarısız olur.  
  
 *Utility.dll* geliştiricileri `Example` , özniteliğini kullanarak sınıfının isteklerini ileterek bunu önleyebilir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> . Öznitelik *Utility.dll* yeni sürümüne uygulanmışsa, sınıfı için istekler, `Example` artık sınıfı içeren derlemeye iletilir. Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.

## <a name="forward-a-type"></a>Bir tür ilet

 Bir türü iletmek için dört adım vardır:  
  
1. Asıl derlemeden hedef derlemeye tür için kaynak kodunu taşıyın.  

2. Türünün bulunması için kullanıldığı derlemede, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> taşınan tür için bir ekleyin. Aşağıdaki kod, taşınan adlı bir tür için özniteliğini gösterir `Example` .  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Artık türü içeren derlemeyi derleyin.  

4. Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin. Örneğin, komut satırından bir C# dosyası derlerken, türü içeren derlemeyi belirtmek için [ **Başvurular** (c# Derleyici seçenekleri)](../../csharp/language-reference/compiler-options/inputs.md#references) seçeneğini kullanın. C++ ' da, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Tür iletme (C++/CLı)](/cpp/windows/type-forwarding-cpp-cli)
- [#using yönergesi](/cpp/preprocessor/hash-using-directive-cpp)
