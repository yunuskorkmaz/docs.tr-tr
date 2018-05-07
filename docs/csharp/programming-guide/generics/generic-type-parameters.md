---
title: Genel Tür Parametreleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 35029b90fb7b905a87055596cf8dcd6a84ef9d36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
 [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
