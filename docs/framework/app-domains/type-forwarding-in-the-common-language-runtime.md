---
title: "Ortak Dil Çalışma Zamanında Tür İletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32dad99e8d5caa7d88fa302a1bea8b83847bfde3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Ortak Dil Çalışma Zamanında Tür İletme
Tür iletme özgün derleme kullanan uygulamaları yeniden derlemenize gerek kalmadan başka bir derlemeye türü taşımanızı sağlar.  
  
 Örneğin, bir uygulama kullandığını varsayın `Example` adlı bir derleme sınıfında `Utility.dll`. Geliştiriciler `Utility.dll` derleme yeniden düzenlemeniz karar verebilirsiniz ve bunlar işlemde taşıma `Example` başka bir derleme sınıfı. Varsa eski sürümünü `Utility.dll` yeni sürümü tarafından değiştirilir `Utility.dll` yardımcı derleme, uygulamayı kullanan ve `Example` sınıfı başarısız konumunu belirleyemediği için `Example` yeni sürümünü sınıfında `Utility.dll`.  
  
 Geliştiriciler `Utility.dll` bu istekleri ileterek önleyebilirsiniz `Example` sınıfı, kullanarak <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> özniteliği. Öznitelik'ın yeni sürümüne uygulanıp uygulanmadığını `Utility.dll`, için istekleri `Example` sınıfı şimdi sınıfı içeren derlemeye iletilir. Var olan uygulamaya yeniden derlenmek normal şekilde çalışmaya devam eder.  
  
> [!NOTE]
>  .NET Framework sürüm 2. 0'da, Visual Basic'te yazılmış derlemelerden türler iletemez. Ancak, Visual Basic ile yazılmış bir uygulama iletilen türleri kullanabilir. Diğer bir deyişle, C# veya C++ kodlanmış bütünleştirilmiş uygulama kullanıyorsa ve bu derleme türünden başka bir derlemeye iletilir, Visual Basic uygulama iletilen türü kullanabilirsiniz.  
  
## <a name="forwarding-types"></a>İletme türleri  
 Bir tür iletme gereken dört adım vardır:  
  
1.  Kaynak kodu türü için özgün derlemeden hedef derlemeye taşıyın.  
  
2.  Türü kullanıldığı yer almasını derlemede eklemek bir <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> taşınmış türü için. Aşağıdaki kod adlı tür özniteliğini gösterir `Example` , taşındı.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Şimdi türünü içeren bütünleştirilmiş kodu derleyin.  
  
4.  Türü artık türünü içeren bütünleştirilmiş başvuru yer almasını kullanıldığı derleme yeniden derleyin. Örneğin, C# dosyasına komut satırından derleme ise kullanın [/Reference (C# Derleyici Seçenekleri)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) türünü içeren bütünleştirilmiş kodun belirtmek için seçeneği. C++'ta kullanmak [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) türünü içeren bütünleştirilmiş kodun belirtmek için kaynak dosyasında yönergesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [Tür İletme (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)  
 [#using yönergesi](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
