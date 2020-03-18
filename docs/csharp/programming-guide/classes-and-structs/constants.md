---
title: Sabitler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 85f6684617b893bdd85eb5b530aa2481941fbc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093558"
---
# <a name="constants-c-programming-guide"></a>Sabitler (C# Programlama Kılavuzu)
Sabitler derleme zamanında bilinen ve programın ömrü boyunca değişmeden değişmez değerlerdir. Sabitler [const](../../language-reference/keywords/const.md) değiştirici ile bildirilir. Yalnızca C# [yerleşik türleri](../../language-reference/builtin-types/built-in-types.md) (hariç) <xref:System.Object?displayProperty=nameWithType>olarak `const`bildirilebilir. Sınıflar, structs ve diziler de dahil olmak üzere `const`kullanıcı tanımlı türleri, olamaz. Çalışma zamanında (örneğin, bir oluşturucuda) bir kez başharfe basılan ve bundan sonra değiştirilemeyen bir sınıf, yapı veya dizi oluşturmak için [yalnızca okunur](../../language-reference/keywords/readonly.md) değiştiriyi kullanın.  
  
 C# yöntemleri, `const` özellikleri veya olayları desteklemez.  
  
 Enum türü, integral yerleşik türleri (örneğin, `int`, `uint` `long`, vb. için) adlandırılmış sabitleri tanımlamanızı sağlar. Daha fazla bilgi için [enum' a](../../language-reference/builtin-types/enum.md)bakın.  
  
 Sabitler beyan edildikleri gibi başharflere alınmalıdır. Örnek:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 Bu örnekte, `months` sabit her zaman 12'dir ve sınıfın kendisi tarafından bile değiştirilemez. Aslında, derleyici C# kaynak kodunda sabit bir tanımlayıcıyla karşılaştığında (örneğin,), `months`gerçek değeri doğrudan ürettiği ara dil (IL) koduna ikame eder. Çalışma zamanında sabitle ilişkili değişken bir adres `const` olmadığından, alanlar başvuruyla geçirilemez ve bir ifadede l değeri olarak görüntülenemez.  
  
> [!NOTE]
> DL'ler gibi diğer kodlarda tanımlanan sabit değerlere atıfta bulunurken dikkatli olun. DLL'nin yeni bir sürümü sabit için yeni bir değer tanımlıyorsa, programınız yeni sürüme karşı yeniden derlenene kadar eski gerçek değeri tutmaya devam eder.  
  
 Aynı türden birden çok sabit aynı anda bildirilebilir, örneğin:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Bir sabiti başlatmak için kullanılan ifade, dairesel bir başvuru oluşturmuyorsa başka bir sabite başvurabilir. Örnek:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Sabitler [genel,](../../language-reference/keywords/public.md) [özel,](../../language-reference/keywords/private.md) [korumalı,](../../language-reference/keywords/protected.md) [dahili,](../../language-reference/keywords/internal.md) [korumalı iç](../../language-reference/keywords/protected-internal.md) veya özel [korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiriciler, sınıfın kullanıcılarının sabite nasıl erişebileceğini tanımlar. Daha fazla bilgi için [Erişim Değiştiriciler'e](./access-modifiers.md)bakın.  
  
 Sabitin değeri türün tüm örnekleri için aynı olduğundan, sabitlere [statik](../../language-reference/keywords/static.md) alanlarmış gibi erişilir. `static` Bunları bildirmek için anahtar sözcüğü kullanmazsınız. Sabiti tanımlayan sınıfta olmayan ifadeler, sabite erişmek için sınıf adını, bir dönemi ve sabitin adını kullanmalıdır. Örnek:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Özellikler](./properties.md)
- [Türler](../types/index.md)
- [Readonly](../../language-reference/keywords/readonly.md)
- [C# Bölüm Bir'de değişmezlik: Değişmezlik Çeşitleri](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
