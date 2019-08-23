---
title: Ortak Dil Çalışma Zamanında Tür İletme
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1b05a5548beb7e7c1f0ec8e96b6e02350318ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921411"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Ortak Dil Çalışma Zamanında Tür İletme
Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.  
  
 Örneğin, bir uygulamanın `Example` sınıfını adlı `Utility.dll`bir derlemede kullandığını varsayalım. Geliştiriciler `Utility.dll` , derlemeyi yeniden düzenleme kararı verebilir ve süreçte, `Example` sınıfı başka bir derlemeye taşıyabilir. Eski sürümü `Utility.dll` `Utility.dll` ve onun yardımcı derlemesi yeni sürümü ile değiştirilirse, sınıfını kullanan `Example` uygulama, `Example` sınıfının yeni sürümünde `Utility.dll`konumlandıramadığı için başarısız olur.  
  
 ' A ait `Utility.dll` geliştiriciler, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> özniteliğini kullanarak `Example` sınıfının isteklerini ileterek bunu önleyebilir. Özniteliği yeni sürümüne `Utility.dll`uygulanmışsa, `Example` sınıfı için istekler, artık sınıfını içeren derlemeye iletilir. Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' de, Visual Basic yazılmış derlemelerden türleri iletemezsiniz. Ancak, Visual Basic yazılmış bir uygulama iletilen türleri kullanabilir. Yani, uygulama veya C# C++içinde kodlanmış bir derlemeyi kullanıyorsa ve bu derlemedeki bir tür başka bir derlemeye iletilirse, Visual Basic uygulama iletilen türü kullanabilir.  
  
## <a name="forwarding-types"></a>İletme türleri  
 Bir türü iletmek için dört adım vardır:  
  
1. Asıl derlemeden hedef derlemeye tür için kaynak kodunu taşıyın.  
  
2. Türünün bulunması için kullanıldığı derlemede, taşınan tür için bir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> ekleyin. Aşağıdaki kod, taşınan adlı `Example` bir tür için özniteliğini gösterir.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3. Artık türü içeren derlemeyi derleyin.  
  
4. Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin. Örneğin, komut satırından bir C# dosya derlerken, türü içeren derlemeyi belirtmek için [/Reference (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın. İçinde C++, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Tür İletme (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using yönergesi](/cpp/preprocessor/hash-using-directive-cpp)
