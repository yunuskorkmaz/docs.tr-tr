---
title: Genel tür parametreleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 096fce3affb9461c57ae9c0ffd57367d1b4349df
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423425"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Genel tür parametreleri (C# Programlama Kılavuzu)

Genel tür veya yöntem tanımını bir tür parametresi bir genel türün örneğini oluşturduğunuzda bir istemci belirtir, belirli bir türü için yer tutucudur. Gibi bir genel sınıf `GenericList<T>` listelenen [genel türlere giriş](../../../csharp/programming-guide/generics/index.md), olarak kullanılamaz-çünkü bu gerçekte bir tür değil; bir tür için bir şema gibi daha fazla. Kullanılacak `GenericList<T>`, istemci kodu bildirme ve bir tür bağımsız değişkeni köşeli ayraç içinde belirterek bir oluşturulmuş tür örneği. Bu belirli bir sınıfın tür bağımsız değişkeni derleyici tarafından tanınan herhangi bir tür olabilir. Herhangi bir sayıda oluşturulan tür örnekleri, her biri farklı tür bağımsız değişkeni, kullanarak aşağıdaki gibi oluşturulabilir:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
Her Bu örneklerin `GenericList<T>`, her geçtiği `T` sınıfı, çalışma zamanında tür bağımsız değişkeni ile değiştirilir. Bir tek sınıf tanımı kullanarak üç ayrı tür açısından güvenli ve verimli nesneler bu değiştirme yoluyla oluşturduk. Bu değiştirme CLR tarafından nasıl gerçekleştirildiğini daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Tür parametresi adlandırma kuralları  
  
- **Yapmak** tamamen kendi kendine açıklama tek harfli adıdır ve açıklayıcı bir ad, değer ekleme değil sürece genel tür parametreleri Tanımlayıcı adlarla adlandırın.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Göz önünde bulundurun** T tek tek harfli türü parametreli türler için tür parametre adı olarak kullanma.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Yapmak** açıklayıcı tür parametresi adlarına "T" ile önek.  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Göz önünde bulundurun** parametre adını bir tür parametresi yerleştirilen kısıtlamaları belirten. Örneğin, bir parametre, için kısıtlı `ISession` çağrılabilir `TSession`.

Kod çözümleme kural [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) tür parametreleri uygun şekilde adlandırıldığından emin olmak için kullanılabilir.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)
- [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
