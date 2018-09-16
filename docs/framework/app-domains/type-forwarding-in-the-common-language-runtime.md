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
ms.openlocfilehash: d25bac953ff68422a1dddc54bdb01b4b4f241cbb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664533"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Ortak Dil Çalışma Zamanında Tür İletme
Tür iletme orijinal derleme kullanan uygulamaları yeniden derlemenize gerek kalmadan bir tür için başka bir derleme taşımanızı sağlar.  
  
 Örneğin, bir uygulamanın kullandığı varsayalım `Example` adlı bir derlemede sınıfı, `Utility.dll`. Geliştiriciler `Utility.dll` derlemeyi yeniden karar verebilirsiniz ve işlemin taşınabilecek `Example` başka bir derleme için sınıf. Varsa eski sürümünü `Utility.dll` yeni sürümü tarafından değiştirilir `Utility.dll` Yardımcısı derlemesi, uygulamayı kullanan ve `Example` sınıfı, bunu konumlandıramadığından başarısız `Example` yeni sürümünü sınıfında `Utility.dll`.  
  
 Geliştiriciler `Utility.dll` bu istekleri ileterek kaçınabilirsiniz `Example` kullanarak sınıf <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> özniteliği. Öznitelik en yeni sürümüne uygulanıp uygulanmadığını `Utility.dll`, için istekleri `Example` sınıfı artık sınıfı içeren derlemeye iletilir. Var olan uygulamayı, normalde, yeniden derleme çalışmaya devam eder.  
  
> [!NOTE]
>  .NET Framework 2.0 sürümünde, Visual Basic'te yazılmış derlemelerden türler iletemez. Ancak, Visual Basic ile yazılan bir uygulamanın iletilen türlerini kullanabilir. Diğer bir deyişle, C# veya C++ ortamında kodlanmış bir derleme uygulama kullanır ve bu derlemeden bir tür için başka bir derleme iletilir, Visual Basic uygulama iletilen türü kullanabilirsiniz.  
  
## <a name="forwarding-types"></a>Tür iletme  
 Bir tür iletme gereken dört adım vardır:  
  
1.  Kaynak kodu türü için özgün derlemeden hedef derlemeye taşıyın.  
  
2.  Derleme türü kullanıldığı yer almasını, ekleme bir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> taşındı türü. Aşağıdaki kod adlı bir tür özniteliğini gösterir `Example` , taşındı.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Artık türü içeren derlemenin derleme.  
  
4.  Türü artık türü içeren derlemeye bir başvuru ile konum için kullanıldığı derlemeyi yeniden derleyin. Örneğin, C# dosyasına komut satırında derleme yapıyorsanız kullanın [/Reference (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) türü içeren derlemenin belirtmek için seçeneği. C++'ta kullanmak [#using](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) türü içeren derlemenin belirtmek için kaynak dosyadaki yönergesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [Tür İletme (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)  
 [#using yönergesi](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
