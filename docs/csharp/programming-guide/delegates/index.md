---
title: Temsilciler-C# Programlama Kılavuzu
description: C# ' deki bir temsilci, bir parametre listesi ve dönüş türü olan yöntemlere başvuran bir türdür. Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.
ms.date: 02/02/2021
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 86f7908501c075881786d16caffdd765b8aaf6b5
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548077"
---
# <a name="delegates-c-programming-guide"></a>Temsilciler (C# Programlama Kılavuzu)

[Temsilci](../../language-reference/builtin-types/reference-types.md) , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eden bir türdür. Bir temsilci oluşturduğunuzda, örneğini uyumlu bir imza ve dönüş türü içeren herhangi bir yöntemle ilişkilendirebilirsiniz. Yöntemi, temsilci örneği aracılığıyla çağırabilirsiniz.

Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır. Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Özel bir yöntem oluşturabilirsiniz ve bir pencere denetimi gibi bir sınıf, belirli bir olay olduğunda yönteminizi çağırabilir. Aşağıdaki örnek, bir temsilci bildirimini gösterir:

[!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]

Temsilci türüyle eşleşen herhangi bir erişilebilir sınıf veya yapıdan alınan herhangi bir yöntem temsilciye atanabilir. Yöntem, statik veya örnek bir yöntem olabilir. Bu esneklik, Yöntem çağrılarını program aracılığıyla değiştirebileceğiniz veya varolan sınıflara yeni kod takbileceğiniz anlamına gelir.

> [!NOTE]
> Yöntem aşırı yükü bağlamında, yöntemin imzası dönüş değeri içermez. Ancak, temsilciler bağlamında, imza dönüş değerini içermez. Başka bir deyişle, bir yöntemin dönüş türü temsilciyle aynı olmalıdır.

Bir yönteme bir parametre olarak başvurma yeteneği, temsilciyi geri çağırma yöntemleri için ideal hale getirir. Uygulamanızdaki iki nesneyi karşılaştıran bir yöntem yazabilirsiniz. Bu yöntem, bir sıralama algoritym için bir temsilci içinde kullanılabilir. Karşılaştırma kodu kitaplıktan ayrı olduğundan, sıralama yöntemi daha genel olabilir.

[İşlev işaretçileri](~/_csharplang/proposals/csharp-9.0/function-pointers.md) , çağırma kuralı üzerinde daha fazla denetime ihtiyaç duyduğunuz benzer senaryolar Için C# 9 ' a eklenmiştir. Bir temsilciyle ilişkili kod, bir temsilci türüne eklenen bir sanal yöntem kullanılarak çağrılır. İşlev işaretçilerini kullanarak farklı kurallar belirtebilirsiniz.

## <a name="delegates-overview"></a>Temsilcilere Genel Bakış

Temsilciler aşağıdaki özelliklere sahiptir:

- Temsilciler C++ işlev işaretçilerine benzerdir, ancak temsilciler tam nesne yönelimli olarak ve üye işlevlerine C++ işaretçilerine benzemekle birlikte, temsilciler hem bir nesne örneğini hem de bir yöntemi kapsüller.
- Temsilciler, yöntemlerin parametre olarak geçirilmesine olanak tanır.
- Temsilciler, geri çağırma yöntemlerini tanımlamak için kullanılabilir.
- Temsilciler birlikte zincirleme yapılabilir; Örneğin, tek bir olay üzerine birden çok yöntem çağrılabilir.
- Yöntemlerin temsilci türüyle tam olarak eşleşmesi gerekmez. Daha fazla bilgi için bkz. [Temsilcilerde varyans kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md).
- Lambda ifadeleri, satır içi kod blokları yazmanın daha kısa bir yoludur. Lambda ifadeleri (bazı bağlamlarda) temsilci türlerine derlenir. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../language-reference/operators/lambda-expressions.md).

## <a name="in-this-section"></a>Bu Bölümde

- [Temsilcileri Kullanma](./using-delegates.md)
- [Arabirimler yerine temsilcilerin ne zaman kullanılacağı (C# Programlama Kılavuzu)](/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))
- [Temsilcilerin Adlandırılmış ve Anonim Yöntemler](./delegates-with-named-vs-anonymous-methods.md)
- [Temsilcilerde Varyans Kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Temsilcileri birleştirme (çok noktaya yayın temsilcileri)](./how-to-combine-delegates-multicast-delegates.md)
- [Temsilci bildirme, oluşturma ve kullanma](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Temsilciler](~/_csharplang/spec/delegates.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri

- C# 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) [: c# 3,0 programcıları için 250 ' den fazla çözüm](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))
- Öğreniminde [Temsilciler ve olaylar](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) [c# 3,0: C# 3,0 temelleri ana](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [C# Programlama Kılavuzu](../index.md)
- [Ekinlikler](../events/index.md)
