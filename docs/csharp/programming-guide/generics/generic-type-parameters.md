---
title: Genel tür parametreleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 27cd89c8e82036bf6353030b4f235c2ebe738e6d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589691"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Genel tür parametreleri (C# Programlama Kılavuzu)

Genel tür veya yöntem tanımında bir tür parametresi, bir istemcinin genel türün bir örneğini oluşturduklarında belirttiği belirli bir tür için yer tutucudur. Genel türlere `GenericList<T>` [giriş](./index.md)bölümünde listelenen gibi genel bir sınıf, gerçekten bir tür olmadığından olduğu gibi kullanılamaz; bu, bir tür için şema gibi bir değer. Kullanmak `GenericList<T>`için, istemci kodu açılı ayraç içinde bir tür bağımsız değişkeni belirterek oluşturulmuş bir tür bildirmelidir ve örneklenmelidir. Bu belirli sınıfın tür bağımsız değişkeni, derleyici tarafından tanınan herhangi bir tür olabilir. Her biri farklı bir tür bağımsız değişkeni kullanılarak oluşturulan herhangi bir sayıda oluşturulmuş tür örneği oluşturulabilir:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
Bu örneklerin `GenericList<T>`her birinde, sınıfındaki her `T` oluşum çalışma zamanında tür bağımsız değişkeniyle değiştirilir. Bu değiştirme yoluyla, tek bir sınıf tanımı kullanarak üç ayrı tür güvenli ve verimli nesne oluşturduk. Bu değiştirmenin CLR tarafından nasıl gerçekleştirildiği hakkında daha fazla bilgi için bkz. [çalışma zamanındaki genel türler](./generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Tür parametresi adlandırma yönergeleri  
  
- Genel tür parametrelerini açıklayıcı adlarla adlandırın, tek bir harf adı tamamen kendi kendine açıklayıcı olamaz ve açıklayıcı bir ad değer eklemez.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- Tek bir harf türü parametresine sahip türler için tür parametre adı olarak T kullanmayı **düşünün** .  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- Önek açıklayıcı tür parametre adlarını "T" ile **yapın** .  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- Parametre adındaki bir tür parametresine yerleştirilmiş olan kısıtlamaları **belirtmeyi düşünün** . Örneğin, ile `ISession` kısıtlanmış bir parametre çağrılabilir `TSession`.

Kod Analizi kuralı [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) , tür parametrelerinin uygun şekilde adlandırılmış olduğundan emin olmak için kullanılabilir.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](./differences-between-cpp-templates-and-csharp-generics.md)
