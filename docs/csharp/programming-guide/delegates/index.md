---
title: Temsilciler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: a0c5592f2f4cca8173f9b777f2c3f14fe468feac
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423314"
---
# <a name="delegates-c-programming-guide"></a>Temsilciler (C# Programlama Kılavuzu)
[Temsilci](../../language-reference/builtin-types/reference-types.md) , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eden bir türdür. Bir temsilci oluşturduğunuzda, örneğini uyumlu bir imza ve dönüş türü içeren herhangi bir yöntemle ilişkilendirebilirsiniz. Yöntemi, temsilci örneği aracılığıyla çağırabilirsiniz.  
  
 Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır. Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Özel bir yöntem oluşturabilirsiniz ve bir pencere denetimi gibi bir sınıf, belirli bir olay olduğunda yönteminizi çağırabilir. Aşağıdaki örnek, bir temsilci bildirimini gösterir:  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Temsilci türüyle eşleşen herhangi bir erişilebilir sınıf veya yapıdan alınan herhangi bir yöntem temsilciye atanabilir. Yöntem, statik veya örnek bir yöntem olabilir. Bu, yöntem çağrılarını programatik olarak değiştirmeyi ve varolan sınıflara yeni kod eklemeyi olanaklı kılar.  
  
> [!NOTE]
> Yöntem aşırı yükü bağlamında, yöntemin imzası dönüş değeri içermez. Ancak, temsilciler bağlamında, imza dönüş değerini içermez. Başka bir deyişle, bir yöntemin dönüş türü temsilciyle aynı olmalıdır.  
  
 Bir yönteme bir parametre olarak başvurma yeteneği, temsilciyi geri çağırma yöntemleri için ideal hale getirir. Örneğin, iki nesneyi karşılaştıran bir yönteme yapılan bir başvuru, bir sıralama algoritmasına bir bağımsız değişken olarak geçirilebilir. Karşılaştırma kodu ayrı bir yordamda olduğundan, sıralama algoritması daha genel bir şekilde yazılabilir.  
  
## <a name="delegates-overview"></a>Temsilcilere Genel Bakış  
 Temsilciler aşağıdaki özelliklere sahiptir:  
  
- Temsilciler C++ işlev işaretçilerine benzer, ancak temsilciler tam nesne yönelimli ve üye işlevlerine yönelik işaretçilerin C++ aksine, temsilciler hem bir nesne örneğini hem de bir yöntemi kapsüller.
  
- Temsilciler, yöntemlerin parametre olarak geçirilmesine olanak tanır.  
  
- Temsilciler, geri çağırma yöntemlerini tanımlamak için kullanılabilir.  
  
- Temsilciler birlikte zincirleme yapılabilir; Örneğin, tek bir olay üzerine birden çok yöntem çağrılabilir.  
  
- Yöntemlerin temsilci türüyle tam olarak eşleşmesi gerekmez. Daha fazla bilgi için bkz. [Temsilcilerde varyans kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- C#sürüm 2,0, kod bloklarının ayrı olarak tanımlanmış bir yöntem yerine parametre olarak geçirilmesine izin veren [Anonim yöntemler](../../language-reference/operators/delegate-operator.md)kavramını sunmuştur. C# 3.0, satır içi kod blokları yazmak için daha kısa bir yol olarak lambda ifadelerini kullanmaya başladı. Hem anonim yöntemler hem de lambda ifadeleri (belirli bağlamlarda) temsilci türleri olarak derlenir. Birlikte, bu özellikler artık anonim işlevler olarak bilinir. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../statements-expressions-operators/lambda-expressions.md).
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [Temsilcileri Kullanma](./using-delegates.md)  
  
- [Arabirimler yerine temsilcilerin ne zaman kullanılacağı (C# Programlama Kılavuzu)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Adlandırılmış ve anonim yöntemler ile Temsilciler](./delegates-with-named-vs-anonymous-methods.md)  
  
- [Temsilcilerde Varyans Kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Nasıl yapılır: temsilcileri birleştirme (çok noktaya yayın temsilcileri)](./how-to-combine-delegates-multicast-delegates.md)  
  
- [Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma](./how-to-declare-instantiate-and-use-a-delegate.md)  

## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Temsilciler](~/_csharplang/spec/delegates.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [ C# : 3,0 programcılar için C# 250 ' den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Öğrenme C# 3,0 C# ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29) ' deki [Temsilciler ve olaylar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) : 3,0 temelleri ana  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
