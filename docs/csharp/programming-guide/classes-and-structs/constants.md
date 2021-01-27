---
title: Sabitler-C# Programlama Kılavuzu
description: C# ' deki sabitler, derleme zamanı değişmez değerleri, program derlendikten sonra değişmez. Yalnızca C# yerleşik türleri sabitler olabilir.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 4783aff8e9424c90e46cb52692a3e645e995d914
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899080"
---
# <a name="constants-c-programming-guide"></a>Sabitler (C# Programlama Kılavuzu)

Sabitler, derleme zamanında bilinen ve programın ömrü boyunca değişmeyen sabit değerlerdir. Sabitler [const](../../language-reference/keywords/const.md) değiştiricisi ile bildirilmiştir. Yalnızca C# [yerleşik türleri](../../language-reference/builtin-types/built-in-types.md) (hariç <xref:System.Object?displayProperty=nameWithType> ) olarak bildirilebilecek `const` . Sınıflar, yapılar ve diziler dahil olmak üzere Kullanıcı tanımlı türler olamaz `const` . Çalışma zamanında bir kez başlatılan bir sınıf, yapı veya dizi oluşturmak için [salt okunur](../../language-reference/keywords/readonly.md) değiştiricisini kullanın (örneğin, bir oluşturucuda) ve bundan sonra değiştirilemez.  
  
 C#, `const` yöntemleri, özellikleri veya olayları desteklemez.  
  
 Sabit listesi türü, integral yerleşik türler (örneğin,, vb.) için adlandırılmış sabitler tanımlamanızı `int` sağlar `uint` `long` . Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).  
  
 Sabitler, bildirildiği için başlatılmalıdır. Örneğin:  
  
 [!code-csharp[Calendar#1](snippets/constants/Calendar.cs#1)]
  
 Bu örnekte, sabit `Months` her zaman 12 ' dir ve sınıfın kendisi tarafından bile değiştirilemez. Aslında, derleyici C# kaynak kodunda bir sabit tanımlayıcıyla karşılaştığında (örneğin, `Months` ), değişmez değer değerini doğrudan ürettiği ara dil (IL) koduna koyar. Çalışma zamanında bir sabitle ilişkili değişken adresi olmadığından, `const` alanlar başvuruya göre geçirilemez ve bir ifadede l değeri olarak görünemez.  
  
> [!NOTE]
> Dll 'Ler gibi başka bir kodda tanımlanan sabit değerlere başvurduğunuzda dikkatli olun. Yeni bir DLL sürümü sabit için yeni bir değer tanımlıyorsa, programınız yeni sürüme yeniden derlenene kadar eski değişmez değeri de tutar.  
  
 Aynı türden birden fazla sabit aynı anda bildirilebilecek, örneğin:  
  
 [!code-csharp[Calendar#2](snippets/constants/Calendar.cs#2)]
  
 Bir sabiti başlatmak için kullanılan ifade, döngüsel başvuru oluşturmayan başka bir sabite başvurabilir. Örneğin:  
  
 [!code-csharp[Calendar#3](snippets/constants/Calendar.cs#3)]
  
 Sabitler, [genel](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının sabitine nasıl erişekullanabileceğinizi tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
 Sabitlere [statik](../../language-reference/keywords/static.md) alanlar gibi erişilir çünkü sabit değeri, türün tüm örnekleri için aynı. `static`Bunları bildirmek için anahtar sözcüğünü kullanmayın. Sabiti tanımlayan sınıfta olmayan ifadeler, sabit erişim için sınıf adı, nokta ve sabitin adını kullanmalıdır. Örneğin:  
  
 [!code-csharp[Calendar#4](snippets/constants/Calendar.cs#4)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Özellikler](./properties.md)
- [Türler](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [C# bölüm bir üzerinde Imleyici kullanılabilirliği: Imleyici kullanılabilirlik çeşitleri](/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
