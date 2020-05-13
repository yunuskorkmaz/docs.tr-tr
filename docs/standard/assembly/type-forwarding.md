---
title: Ortak dil çalışma zamanında tür iletme
description: Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir .NET derlemesine taşımanızı sağlar.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f0be61bd4ce88569e22a350a9ea9490d67e74ff3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378590"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Ortak dil çalışma zamanında tür iletme
Tür iletme, özgün derlemeyi kullanan uygulamaları yeniden derlemek zorunda kalmadan bir türü başka bir derlemeye taşımanızı sağlar.  
  
 Örneğin, bir uygulamanın `Example` sınıfının *Utility. dll*adlı bir derlemede kullandığını varsayalım. *Utility. dll* ' nin geliştiricileri derlemeyi yeniden düzenleme kararı verebilir ve süreçte `Example` sınıfı başka bir derlemeye taşıyabilir. *Utility* . dll ' nin eski sürümü *Utility. dll* ' nin yeni sürümü ve yardımcı bütünleştirilmiş kodu tarafından değiştirilirse, sınıfını kullanan uygulama, `Example` `Example` sınıfının yeni bir *Utility. dll*sürümünde konumlandıramadığı için başarısız olur.  
  
 *Utility. dll* ' nin geliştiricileri `Example` , özniteliğini kullanarak, sınıfının isteklerini ileterek bunu önleyebilir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> . Özniteliği, *Utility. dll*' nin yeni sürümüne uygulanmışsa, `Example` sınıfının istekleri artık sınıfı içeren derlemeye iletilir. Mevcut uygulama, yeniden derleme yapılmadan normal şekilde çalışmaya devam eder.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' de, Visual Basic yazılmış derlemelerden türleri iletemezsiniz. Ancak, Visual Basic yazılmış bir uygulama iletilen türleri kullanabilir. Yani, uygulama C# veya C++ dilinde kodlanmış bir derlemeyi kullanıyorsa ve bu derlemedeki bir tür başka bir derlemeye iletilirse, Visual Basic uygulama iletilen türü kullanabilir.  
  
## <a name="forward-types"></a>İleri türleri  
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

4. Türü içeren derlemeye bir başvuru ile, türü bulunan derlemeyi yeniden derleyin. Örneğin, komut satırından bir C# dosyası derlerken, türü içeren derlemeyi belirtmek için [-Reference (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneğini kullanın. C++ ' da, türü içeren derlemeyi belirtmek için kaynak dosyadaki [#using](/cpp/preprocessor/hash-using-directive-cpp) yönergesini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Tür iletme (C++/CLı)](/cpp/windows/type-forwarding-cpp-cli)
- [#using yönergesi](/cpp/preprocessor/hash-using-directive-cpp)
