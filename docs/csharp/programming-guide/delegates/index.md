---
title: Delegeler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: c0f28716926d4c9d74cde58fd00e27d1fdfa7ce1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75705372"
---
# <a name="delegates-c-programming-guide"></a>Temsilciler (C# Programlama Kılavuzu)
[Temsilci,](../../language-reference/builtin-types/reference-types.md) belirli bir parametre listesi ve dönüş türüne sahip yöntemlere yapılan başvuruları temsil eden bir türdür. Bir temsilci oluşturduğunuzda, örneğini uyumlu bir imza ve dönüş türü içeren herhangi bir yöntemle ilişkilendirebilirsiniz. Yöntemi, temsilci örneği aracılığıyla çağırabilirsiniz.  
  
 Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır. Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Özel bir yöntem oluşturabilirsiniz ve bir pencere denetimi gibi bir sınıf, belirli bir olay olduğunda yönteminizi çağırabilir. Aşağıdaki örnek, bir temsilci bildirimini gösterir:  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Temsilci türüyle eşleşen herhangi bir erişilebilir sınıf veya yapıdan alınan herhangi bir yöntem temsilciye atanabilir. Yöntem, statik veya örnek bir yöntem olabilir. Bu, yöntem çağrılarını programatik olarak değiştirmeyi ve varolan sınıflara yeni kod eklemeyi olanaklı kılar.  
  
> [!NOTE]
> Yöntem aşırı yükü bağlamında, yöntemin imzası dönüş değeri içermez. Ancak, temsilciler bağlamında, imza dönüş değerini içermez. Başka bir deyişle, bir yöntemin dönüş türü temsilciyle aynı olmalıdır.  
  
 Bir yönteme bir parametre olarak başvurma yeteneği, temsilciyi geri çağırma yöntemleri için ideal hale getirir. Örneğin, iki nesneyi karşılaştıran bir yönteme yapılan bir başvuru, bir sıralama algoritmasına bir bağımsız değişken olarak geçirilebilir. Karşılaştırma kodu ayrı bir yordamda olduğundan, sıralama algoritması daha genel bir şekilde yazılabilir.  
  
## <a name="delegates-overview"></a>Temsilcilere Genel Bakış  
 Temsilciler aşağıdaki özelliklere sahiptir:  
  
- Temsilciler C++ işlev işaretçilerine benzer, ancak temsilciler tamamen nesne yönelimlidir ve üye işlevlere c++ işaretçilerinin aksine, temsilciler hem nesne örneğini hem de yöntemi kapsüller.
  
- Temsilciler, yöntemlerin parametre olarak geçirilmesine olanak tanır.  
  
- Temsilciler, geri çağırma yöntemlerini tanımlamak için kullanılabilir.  
  
- Temsilciler birlikte zincirleme yapılabilir; Örneğin, tek bir olay üzerine birden çok yöntem çağrılabilir.  
  
- Yöntemlerin temsilci türüyle tam olarak eşleşmesi gerekmez. Daha fazla bilgi için, [Temsilcilerde Varyans Kullanma'ya](../concepts/covariance-contravariance/using-variance-in-delegates.md)bakın.  
  
- C# sürüm 2.0, kod bloklarının ayrı ayrı tanımlanmış bir yöntem yerine parametre olarak geçirilmesine olanak tanıyan [anonim yöntemler](../../language-reference/operators/delegate-operator.md)kavramını tanıttı. C# 3.0, satır içi kod blokları yazmak için daha kısa bir yol olarak lambda ifadelerini kullanmaya başladı. Hem anonim yöntemler hem de lambda ifadeleri (belirli bağlamlarda) temsilci türleri olarak derlenir. Birlikte, bu özellikler artık anonim işlevler olarak bilinir. Lambda ifadeleri hakkında daha fazla bilgi için [Lambda ifadeleri'ne](../statements-expressions-operators/lambda-expressions.md)bakın.
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [Temsilcileri Kullanma](./using-delegates.md)  
  
- [Arabirimler Yerine Temsilci Ne Zaman Kullanılır (C# Programlama Kılavuzu)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Adlandırılmış ve Anonim Yöntemler ile Temsilciler](./delegates-with-named-vs-anonymous-methods.md)  
  
- [Temsilcilerde Varyans Kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Temsilciler nasıl birleştirilir (Çok Noktaya Yayın Temsilcileri)](./how-to-combine-delegates-multicast-delegates.md)  
  
- [Temsilci bildirme, oluşturma ve kullanma](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Temsilciler'e](~/_csharplang/spec/delegates.md) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 C# 3.0 Yemek Kitabında [Delegeler, Etkinlikler ve Lambda İfadeleri,](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [Üçüncü Baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [C#](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) 3.0 Öğrenmede Delegeler ve [Etkinlikler: C# 3.0'ın temellerinde ustalaşma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
