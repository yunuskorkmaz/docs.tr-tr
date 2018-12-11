---
title: Genel tür parametreleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8b9e040beea0590320a34d35ca323374f357bf2f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238201"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Genel Tür Parametreleri (C# Programlama Kılavuzu)
Genel tür veya yöntem tanımını bir tür parametreleri olan bir istemci olduğunda bunlar genel türünde bir değişken örneği belirtir, belirli bir tür için bir yer tutucu. Gibi bir genel sınıf `GenericList<T>` listelenen [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md), olarak kullanılamaz-çünkü bu gerçekte bir tür değil; bir tür için bir şema gibi daha fazla. Kullanılacak `GenericList<T>`, istemci kodu bildirme ve bir tür bağımsız değişkeni köşeli ayraç içinde belirterek bir oluşturulmuş tür örneği. Bu belirli bir sınıfın tür bağımsız değişkeni derleyici tarafından tanınan herhangi bir tür olabilir. Herhangi bir sayıda oluşturulan tür örnekleri, her biri farklı tür bağımsız değişkeni, kullanarak aşağıdaki gibi oluşturulabilir:  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 Her Bu örneklerin `GenericList<T>`, her geçtiği `T` sınıfı, çalışma zamanında tür bağımsız değişkeni ile değiştirilecektir. Bir tek sınıf tanımı kullanarak üç ayrı tür açısından güvenli ve verimli nesneler bu değiştirme yoluyla oluşturduk. Bu değiştirme CLR tarafından nasıl gerçekleştirildiğini daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Tür parametresi adlandırma kuralları  
  
-   **Yapmak** tamamen kendi kendine açıklama tek harfli adıdır ve açıklayıcı bir ad, değer ekleme değil sürece genel tür parametreleri Tanımlayıcı adlarla adlandırın.  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Göz önünde bulundurun** T tek tek harfli türü parametreli türler için tür parametre adı olarak kullanma.  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Yapmak** açıklayıcı tür parametresi adlarına "T" ile önek.  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Göz önünde bulundurun** parametre adını bir tür parametresi yerleştirilen kısıtlamaları belirten. Örneğin, bir parametre, için kısıtlı `ISession` çağrılabilir `TSession`.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Collections.Generic>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
- [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
