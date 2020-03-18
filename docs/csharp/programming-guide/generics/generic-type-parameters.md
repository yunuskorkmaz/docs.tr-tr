---
title: Genel Tip Parametreler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712188"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Genel tür parametreleri (C# Programlama Kılavuzu)

Genel bir tür veya yöntem tanımında, tür parametresi, istemcinin genel türün bir örneğini oluştururken belirttiği belirli bir tür için bir yer tutucudur. Genel Lere `GenericList<T>` [Giriş'te](./index.md)listelenen genel bir sınıf, gerçekten bir tür olmadığı için olduğu gibi kullanılamaz; daha çok bir tür için bir plan gibidir. Kullanmak `GenericList<T>`için, istemci kodu açı parantez içinde bir tür bağımsız değişkeni belirterek oluşturulmuş bir türü bildirmek ve anlık olmalıdır. Bu sınıfın tür bağımsız değişkeni derleyici tarafından tanınan herhangi bir tür olabilir. Oluşturulan tür örnekleri, her biri farklı bir tür bağımsız değişkeni kullanarak, aşağıdaki gibi oluşturulabilir:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
Bu örneklerin her `GenericList<T>`birinde, sınıftaki `T` her oluşum çalışma zamanında tür bağımsız değişkeni ile ikame edilir. Bu ikame sayesinde, tek bir sınıf tanımı kullanarak üç ayrı tür güvenli ve verimli nesneler oluşturduk. Bu ikame clr tarafından nasıl gerçekleştirildiği hakkında daha fazla bilgi [için, Run Time'daki Genel Bilgiler'e](./generics-in-the-run-time.md)bakın.  
  
## <a name="type-parameter-naming-guidelines"></a>Parametre adlandırma yönergeleri yazın  
  
- **Do** Tek bir harf adı tamamen açıklayıcı ve açıklayıcı bir ad değer eklemez sürece, açıklayıcı adlarla genel tür parametreleri adlandırın.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- Tek harf türü parametresi olan türler için tür parametresi adı olarak T'yi kullanmayı **düşünün.**  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- "T" ile açıklayıcı tür parametre adları önek **yapın.**  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- Parametre adına bir tür parametresine yerleştirilen kısıtlamaları belirtmeyi **düşünün.** Örneğin, sınırlandırılmış `ISession` bir parametre . `TSession`

Kod çözümleme kuralı [CA1715,](/visualstudio/code-quality/ca1715) tür parametrelerinin uygun şekilde adlandırılmasını sağlamak için kullanılabilir.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](./differences-between-cpp-templates-and-csharp-generics.md)
