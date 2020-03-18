---
title: Kısmi Sınıflar ve Yöntemler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 50b192d5a7416a982f41d0c3ac13e9c1bfe3397c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399821"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)

Bir [sınıfın](../../language-reference/keywords/class.md)tanımını, bir [yapıyı,](../../language-reference/builtin-types/struct.md) [arabirimi](../../language-reference/keywords/interface.md) veya yöntemi iki veya daha fazla kaynak dosya üzerinde bölmek mümkündür. Her kaynak dosya tür veya yöntem tanımının bir bölümünü içerir ve uygulama derlendiğinde tüm parçalar birleştirilir.

## <a name="partial-classes"></a>Kısmi Sınıflar

Sınıf tanımının bölünmesi nin arzu edilen birkaç durum vardır:

- Büyük projeler üzerinde çalışırken, bir sınıfı ayrı dosyalara yaymak, birden çok programcının aynı anda üzerinde çalışmasını sağlar.

- Otomatik olarak oluşturulan kaynakla çalışırken, kod kaynak dosyasını yeniden oluşturmak zorunda kalmadan sınıfa eklenebilir. Visual Studio, Windows Formları, Web hizmeti paketleyici kodu ve benzeri oluştururken bu yaklaşımı kullanır. Visual Studio tarafından oluşturulan dosyayı değiştirmek zorunda kalmadan bu sınıfları kullanan kod oluşturabilirsiniz.

- Bir sınıf tanımını bölmek için, burada gösterildiği gibi [kısmi](../../language-reference/keywords/partial-type.md) anahtar kelime değiştiricisini kullanın:

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

Anahtar `partial` kelime, sınıfın diğer bölümlerinin, yapının veya arabirimin ad alanında tanımlanabileceğini belirtir. Tüm parçalar anahtar `partial` kelimeyi kullanmalıdır. Tüm parçalar, son türü oluşturmak için derleme zamanında kullanılabilir olmalıdır. Tüm parçalar , , `public` `private`ve benzeri gibi aynı erişilebilirlik olmalıdır.

Herhangi bir bölüm soyut olarak ilan edilirse, o zaman tüm tür soyut olarak kabul edilir. Herhangi bir parça mühürlü olarak ilan edilirse, o zaman tüm türü mühürlü olarak kabul edilir. Herhangi bir bölüm bir taban türü bildirirse, tüm tür o sınıfı devralır.

Taban sınıf belirten tüm bölümler kabul edilmelidir, ancak taban sınıfı atlayan parçalar yine de taban türü devralır. Parçalar farklı temel arabirimleri belirtebilir ve son tür tüm kısmi bildirimleri tarafından listelenen tüm arabirimleri uygular. Kısmi tanımda bildirilen herhangi bir sınıf, yapı veya arayüz üyesi diğer tüm bölümlerde kullanılabilir. Son tür derleme zamanında tüm parçaların kombinasyonudur.

> [!NOTE]
> `partial` Değiştirici temsilci veya numaralandırma beyannamelerinde kullanılamaz.

Aşağıdaki örnek, iç içe geçtikleri tür kısmi olmasa bile, iç içe geçme türlerinin kısmi olabileceğini gösterir.

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

Derleme zamanında, kısmi tür tanımlarının öznitelikleri birleştirilir. Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

Bunlar aşağıdaki beyanlara eşdeğerdir:

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

Aşağıdakitüm kısmi tür tanımlarından birleştirilir:

- XML açıklamaları

- arabirimler

- genel tür parametre öznitelikleri

- class öznitelikleri

- üyeler

Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

Bunlar aşağıdaki beyanlara eşdeğerdir:

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a>Kısıtlamalar

Kısmi sınıf tanımlarıyla çalışırken uymanız gereken birkaç kural vardır:

- Aynı türdeki parçalar olması amaçlandığı tüm kısmi tür `partial`tanımları ile değiştirilmelidir. Örneğin, aşağıdaki sınıf bildirimleri bir hata oluşturur:

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- `partial` Değiştirici yalnızca anahtar kelimelerden `class`hemen `struct`önce `interface`görünebilir, veya .

- İç içe gelen kısmi türler, aşağıdaki örnekte gösterildiği gibi kısmi tür tanımlarında izin verilir:

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- Aynı türde parçalar olması gereken tüm kısmi tür tanımları aynı montaj ve aynı modül (.exe veya .dll dosyası) tanımlanmalıdır. Kısmi tanımlar birden çok modülü kaplayamaz.

- Sınıf adı ve genel tür parametreleri tüm kısmi tür tanımlarında eşleşmelidir. Genel türleri kısmi olabilir. Her kısmi bildirim aynı sırada aynı parametre adlarını kullanmalıdır.

- Kısmi tür tanımında aşağıdaki anahtar kelimeler isteğe bağlıdır, ancak bir kısmi tür tanımında mevcutsa, aynı tür için başka bir kısmi tanımda belirtilen anahtar kelimelerle çakışamaz:

  - [Kamu](../../language-reference/keywords/public.md)

  - [Özel](../../language-reference/keywords/private.md)

  - [protected](../../language-reference/keywords/protected.md)

  - [Iç](../../language-reference/keywords/internal.md)

  - [Soyut](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - taban sınıfı

  - [yeni](../../language-reference/keywords/new-modifier.md) değiştirici (iç içe parçalar)

  - genel kısıtlamalar

Daha fazla bilgi [için, Tür Parametreleri üzerindeki Kısıtlamalar'a](../generics/constraints-on-type-parameters.md)bakın.

## <a name="example-1"></a>Örnek 1

### <a name="description"></a>Açıklama

Aşağıdaki örnekte, alanların ve sınıfın oluşturucusu, `Coords`bir kısmi sınıf tanımında beyan `PrintCoords`edilir ve üye, başka bir kısmi sınıf tanımında bildirilir.

### <a name="code"></a>Kod

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a>Örnek 2

### <a name="description"></a>Açıklama

Aşağıdaki örnek, kısmi yapı ve arabirimler de geliştirebileceğinizi gösterir.

### <a name="code"></a>Kod

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a>Kısmi Yöntemler

Kısmi bir sınıf veya yapı kısmi bir yöntem içerebilir. Sınıfın bir bölümü yöntemin imzasını içerir. İsteğe bağlı bir uygulama aynı parçada veya başka bir bölümde tanımlanabilir. Uygulama sağlanmıyorsa, yöntem ve yönteme yapılan tüm çağrılar derleme zamanında kaldırılır.

Kısmi yöntemler, bir sınıfın bir bölümünün uygulayıcısının bir olaya benzer bir yöntem tanımlamasını sağlar. Sınıfın diğer bölümünün uygulayıcısı yöntemi uygulayıp uygulamamaya karar verebilir. Yöntem uygulanmazsa, derleyici yöntem imzasını ve yönteme yapılan tüm çağrıları kaldırır. Çağrılardaki bağımsız değişkenlerin değerlendirilmesinden kaynaklanan sonuçlar da dahil olmak üzere yönteme yapılan çağrıların çalışma zamanında hiçbir etkisi yoktur. Bu nedenle, kısmi sınıftaki herhangi bir kod, uygulama sağlanmasa bile kısmi bir yöntemi serbestçe kullanabilir. Yöntem çağrıldıysa ancak uygulanmazsa derleme zamanı veya çalışma zamanı hataları olmaz.

Kısmi yöntemler, özellikle oluşturulan kodu özelleştirmenin bir yolu olarak yararlıdır. Oluşturulan kodun yöntemi çağırabilmesi için bir yöntem adı ve imzasının ayrılmasına izin verirler, ancak geliştirici yöntemi uygulayıp uygulamamaya karar verebilir. Kısmi sınıflar gibi, kısmi yöntemler de bir kod oluşturucusu tarafından oluşturulan kodu ve insan geliştirici tarafından oluşturulan kodun çalışma süresi maliyetleri olmadan birlikte çalışmasını sağlar.

Kısmi yöntem bildirimi iki bölümden oluşur: tanım ve uygulama. Bunlar kısmi sınıfın ayrı bölümlerinde veya aynı bölümde olabilir. Uygulama bildirimi yoksa, derleyici hem tanımlayıcı bildirimi hem de yönteme yapılan tüm çağrıları en iyi duruma getirerek uzaklara gider.

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- Kısmi yöntem bildirimleri bağlamsal anahtar kelime [kısmi](../../language-reference/keywords/partial-type.md) ile başlamalı ve yöntem [geçersiz](../../language-reference/builtin-types/void.md)dönmelidir.

- Kısmi yöntemler [olabilir](../../language-reference/keywords/in-parameter-modifier.md) veya [ref](../../language-reference/keywords/ref.md) ama [parametreleri dışarı](../../language-reference/keywords/out-parameter-modifier.md) değil.

- Kısmi yöntemler örtülü olarak [özeldir](../../language-reference/keywords/private.md)ve bu nedenle [sanal](../../language-reference/keywords/virtual.md)olamazlar.

- Kısmi yöntemler [extern](../../language-reference/keywords/extern.md)olamaz , çünkü vücudun varlığı onlar tanımlayan veya uygulayan olup olmadığını belirler.

- Kısmi [yöntemlerstatik](../../language-reference/keywords/static.md) ve [güvensiz](../../language-reference/keywords/unsafe.md) değiştiriciler olabilir.

- Kısmi yöntemler genel olabilir. Kısıtlamalar tanımlayıcı kısmi yöntem bildirimine konur ve isteğe bağlı olarak uygulama bildiriminde yinelenebilir. Parametre ve tür parametresi adları, uygulama bildiriminde tanımlayıcı dakiyle aynı olmak zorunda değildir.

- Tanımlanmış ve uygulanmış kısmi bir yönteme [temsilci](../../language-reference/builtin-types/reference-types.md) atayabilirsiniz, ancak yalnızca tanımlanmış kısmi bir yönteme temsilci yapamazsınız.

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Kısmi türleri](~/_csharplang/spec/classes.md#partial-types) görün. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar](./classes.md)
- [Yapı türleri](../../language-reference/builtin-types/struct.md)
- [Arabirimler](../interfaces/index.md)
- [partial (Tür)](../../language-reference/keywords/partial-type.md)
