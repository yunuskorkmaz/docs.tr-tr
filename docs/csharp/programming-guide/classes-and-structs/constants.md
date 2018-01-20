---
title: "Sabitler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 86c9371a6a82c4034b7bdf279e7b205cfcc84bea
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="constants-c-programming-guide"></a>Sabitler (C# Programlama Kılavuzu)
Derleme zamanında bilinen ve program ömrü için değiştirmeyin değişmez değerler sabittir. Sabitler ile bildirildiğinde [const](../../../csharp/language-reference/keywords/const.md) değiştiricisi. Yalnızca C# yerleşik türleri (hariç <xref:System.Object?displayProperty=nameWithType>) olarak bildirilmelidir `const`. Yerleşik türler listesi için bkz: [yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md). Sınıflar, yapılar ve diziler dahil olmak üzere, kullanıcı tanımlı türler olamaz `const`. Kullanım [readonly](../../../csharp/language-reference/keywords/readonly.md) sınıf, yapı veya çalışma zamanında (örneğin, bir kurucu) ve bundan sonra bir kez başlatılan dizi oluşturmak için değiştiricisi değiştirilemez.  
  
 C# desteklemiyor `const` yöntemler, özellikler veya olayları.  
  
 Enum türü tam sayı yerleşik türleri için adlandırılmış sabitler tanımlamanızı sağlar (örneğin `int`, `uint`, `long`, vb.). Daha fazla bilgi için bkz: [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Bunlar bildirilir olarak sabit başlatılması gerekir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 Bu örnekte, sabit `months` her zaman 12 ise ve hatta sınıfı tarafından kendisini değiştirilemez. Aslında, derleyici karşılaştığında C# kaynak kodu sabit bir tanımlayıcı (örneğin, `months`), doğrudan bu üretir Ara dile (IL) koda hazır değeri ile değiştirir. Çalışma zamanında bir sabit ile ilişkili bir değişken adresi olmadığından `const` alanları başvuruya göre geçirilemez ve l değeri bir ifade olarak yer alamaz.  
  
> [!NOTE]
>  DLL'ler gibi diğer kodda tanımlanan sabit değerleri başvurduğunuzda dikkatli olun. DLL yeni bir sürümü sabiti için yeni bir değer tanımlıyorsa, yeni sürüm karşı derlenmiştir kadar programınızı eski değişmez değer hala tutun.  
  
 Aynı türde birden fazla sabitleri aynı anda örneğin bildirilebilir:  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 Bir sabit başlatmak için kullanılan ifade bir döngüsel başvuru oluşturmuyorsa için başka bir sabit başvurabilir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Sabitler işaretlenir olarak [ortak](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [içkorumalı](../../../csharp/language-reference/keywords/protected-internal.md)veya [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md). Bu erişim değiştiricileri sınıfı kullanıcılarının sabiti nasıl erişebileceğinizi tanımlayın. Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bunlar değilmiş gibi sabitleri erişilir [statik](../../../csharp/language-reference/keywords/static.md) sabit değeri türündeki tüm örnekler için aynı olduğundan alanları. Kullanmaz `static` bunları bildirmek için anahtar sözcüğü. Sabit tanımlar sınıfında olmayan ifadeleri sabiti erişmek için sınıf adı, bir süre ve sabit adını kullanmanız gerekir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)  
 [C# girişi bölüm bir: girişi türleri](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
