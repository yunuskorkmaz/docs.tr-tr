---
title: Sabitler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: b723bb23559f88e7498c22295a6b2f70312461fc
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241937"
---
# <a name="constants-c-programming-guide"></a>Sabitler (C# Programlama Kılavuzu)
Program süresince değiştirmeyin ve derleme zamanında bilinen değişmez değerler sabittir. Sabitler ile bildirilmiş [const](../../../csharp/language-reference/keywords/const.md) değiştiricisi. Yalnızca C# yerleşik türleri (hariç <xref:System.Object?displayProperty=nameWithType>) olarak bildirilebilir `const`. Yerleşik türler bir listesi için bkz. [yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md). Kullanıcı tanımlı türler, sınıflar, yapılar ve diziler de dahil olmak üzere olamaz `const`. Kullanım [salt okunur](../../../csharp/language-reference/keywords/readonly.md) değiştiricisi bir sınıf, yapı veya çalışma zamanı (örneğin, bir oluşturucu) ve bundan sonra bir kez başlatılan bir dizi oluşturmak için değiştirilemez.  
  
 C# desteklemiyor `const` yöntemleri, özellikleri veya olayları.  
  
 Enum türü yerleşik tam sayı türleri için adlandırılmış sabitler tanımlamanızı sağlar (örneğin `int`, `uint`, `long`, vb.). Daha fazla bilgi için [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Sabitler bildirildikleri olarak başlatılması gerekir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 Bu örnekte, sabit `months` her zaman 12 ve sınıfın kendisi bile değiştirilemez. Aslında, derleyici karşılaştığında C# kaynak kodundaki sabit bir tanımlayıcı (örneğin, `months`), doğrudan ürettiği Ara dil (IL) koda değişmez değerin yerini alır. Çalışma zamanında, bir sabit ile ilişkili hiçbir değişken adresi olduğundan `const` alanları başvuruyla geçirildi ve bir l-değeri bir ifade olarak yer alamaz.  
  
> [!NOTE]
>  DLL'leri gibi başka bir kod içinde tanımlanan sabit değerler başvurduğunuzda dikkatli olun. Yeni bir DLL sürümünü sabiti için yeni bir değer tanımlıyorsa, yeni sürüme karşı yeniden derlenen kadar programınızı eski değişmez değer hala tutun.  
  
 Aynı türde birden fazla sabit aynı zamanda, örneğin bildirilebilir:  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 Döngüsel başvuru oluşturmuyorsa sabit başlatmak için kullanılan ifade başka bir sabite başvurabilir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Sabitler olarak işaretlenebilir [genel](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [içkorumalı](../../../csharp/language-reference/keywords/protected-internal.md)veya [korunan özel](../../../csharp/language-reference/keywords/private-protected.md). Bu erişim değiştiricileri kullanıcıları sınıfının sabiti nasıl erişebileceğiniz tanımlayın. Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bunlar gibi sabitleri erişilir [statik](../../../csharp/language-reference/keywords/static.md) sabit değer türündeki tüm örnekler için aynı olduğu için alanlar. Seçeneğini kullanmaz `static` bunları bildirmek için anahtar sözcüğü. Sabiti tanımlar sınıfında yer almayan ifadeler sabit erişmek için sınıf adı, bir süre ve sabiti adını kullanmanız gerekir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Türler](../../../csharp/programming-guide/types/index.md)  
- [readonly](../../../csharp/language-reference/keywords/readonly.md)  
- [İçinde değiştirilemezlik C# birinci bölüm: Değiştirilemezlik türleri](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
