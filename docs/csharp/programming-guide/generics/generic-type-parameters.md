---
title: "Genel Tür Parametreleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b32db7eb6e7788167e110a91726e9dbfe19f31ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-type-parameters-c-programming-guide"></a>Genel Tür Parametreleri (C# Programlama Kılavuzu)
Genel tür veya yöntem tanımı, bir tür parametreleri bir yer tutucudur belirli türünün bir istemci olduğunda bunlar genel türünde bir değişken örneğini belirtir. Genel sınıf, gibi `GenericList<T>` listelenen [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md), olarak kullanılamaz-çünkü bunu gerçekten bir tür değil; bir türü şeması gibi daha fazla. Kullanılacak `GenericList<T>`, istemci kodu bildirme ve yapılandırılmış bir tür, tür bağımsız değişkeni köşeli ayraç içinde belirterek örneği. Tür bağımsız değişkeni belirli Bu sınıf için derleyici tarafından tanınan herhangi bir türü olabilir. Herhangi bir sayıda oluşturulan türü örnekleri, her biri farklı tür bağımsız değişkeni aşağıdaki gibi kullanarak oluşturulabilir:  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 Her bu örneklerinin `GenericList<T>`, her geçtiği `T` sınıfında çalışma zamanında tür bağımsız değişkeni ile değiştirilecektir. Bu değiştirme yoluyla tek sınıf tanımını kullanarak üç ayrı tür kullanımı uyumlu ve verimli nesneleri oluşturduk. Bu değiştirme CLR tarafından nasıl gerçekleştirildiğini daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Adlandırma yönergeleri tür parametresi  
  
-   **Yapmak** tamamen kendi kendine açıklama ve açıklayıcı bir ad, değer Ekle değil tek harf adı sürece genel tür parametreleri açıklayıcı adlar ile adı.  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Göz önünde bulundurun** T tek tek harf tür parametresi türleriyle türü parametre adı olarak kullanma.  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Yapmak** tanımlayıcı türü parametre adları "T" ile önek.  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Göz önünde bulundurun** kısıtlamaları belirten yerleştirilen bir tür parametresi parametre adına üzerinde. Örneğin, bir parametre kısıtlı için `ISession` çağrılabilir `TSession`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel türler](../../../csharp/programming-guide/generics/index.md)  
 [C++ şablonları ve C# genel türleri arasındaki farklar](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
