---
title: Kısmi sınıflar ve yöntemler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: ea8d95c41df236897761ace1062ec325a069d52b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714741"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Kısmi Sınıflar ve Yöntemler (C# Programlama Kılavuzu)

Bir [sınıfın](../../language-reference/keywords/class.md)tanımını, bir [yapıyı](../../language-reference/keywords/struct.md), [arabirimi](../../language-reference/keywords/interface.md) veya bir yöntemi iki veya daha fazla kaynak dosya üzerinde ayırmak mümkündür. Her kaynak dosya, tür veya yöntem tanımının bir bölümünü içerir ve uygulama derlendiğinde tüm parçalar birleştirilir.

## <a name="partial-classes"></a>Kısmi sınıflar

Bir sınıf tanımını bölmek istenen birkaç durum vardır:

- Büyük projeler üzerinde çalışırken, bir sınıfın ayrı dosyalar üzerinde yayılması, birden fazla programcıların aynı anda üzerinde çalışmasını sağlar.

- Otomatik olarak oluşturulan kaynakla çalışırken, kaynak dosyayı yeniden oluşturmak zorunda kalmadan kod sınıfa eklenebilir. Visual Studio, Windows Forms, Web hizmeti sarmalayıcı kodu vb. oluşturduğunda bu yaklaşımı kullanır. Visual Studio tarafından oluşturulan dosyayı değiştirmek zorunda kalmadan, bu sınıfları kullanan kod oluşturabilirsiniz.

- Bir sınıf tanımını ayırmak için, burada gösterildiği gibi [kısmi](../../language-reference/keywords/partial-type.md) anahtar sözcük değiştiricisini kullanın:

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

`partial` anahtar sözcüğü, sınıfın, yapının veya arabirimin diğer bölümlerinin ad alanında tanımlanamayacağını belirtir. Tüm parçaların `partial` anahtar sözcüğünü kullanması gerekir. Son türü oluşturmak için tüm parçalar derleme zamanında kullanılabilir olmalıdır. Tüm parçalar `public`, `private`vb. gibi aynı erişilebilirliği içermelidir.

Herhangi bir bölüm soyut olarak bildirilirse, tüm tür soyut olarak değerlendirilir. Herhangi bir bölüm Sealed olarak bildirilirse, tüm tür Sealed olarak değerlendirilir. Herhangi bir parça bir temel tür bildiriyorsa, tüm tür o sınıfı devralır.

Bir temel sınıf belirten tüm parçalar kabul etmelidir, ancak temel bir sınıfı atlayan parçalar hala temel türü miras alır. Parçalar farklı temel arabirimler belirtebilir ve son tür tüm kısmi bildirimlerin listelebileceği tüm arabirimleri uygular. Kısmi bir tanımda belirtilen herhangi bir sınıf, yapı veya arabirim üyesi diğer tüm parçalar için kullanılabilir. Son tür derleme zamanında tüm parçaların birleşimidir.

> [!NOTE]
> `partial` değiştiricisi temsilci veya numaralandırma bildirimlerinde kullanılamıyor.

Aşağıdaki örnek iç içe geçmiş türlerin kısmen, iç içe yerleştirilmiş olması durumunda bile kısmi bir tür olduğunu gösterir.

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

Derleme zamanında, kısmi tür tanımlarının öznitelikleri birleştirilir. Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

Bunlar aşağıdaki bildirimlerle eşdeğerdir:

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

Aşağıdakiler tüm kısmi tür tanımlarından birleştirilir:

- XML açıklamaları

- arabirimler

- Genel tür parametre öznitelikleri

- class öznitelikleri

- üyeler

Örneğin, aşağıdaki bildirimleri göz önünde bulundurun:

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

Bunlar aşağıdaki bildirimlerle eşdeğerdir:

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a>{1&gt;Kısıtlamalar&lt;1}

Kısmi sınıf tanımlarına çalışırken izlenecek birkaç kural vardır:

- Aynı türdeki parçalar olması amaçlanan tüm kısmi tür tanımlarının `partial`ile değiştirilmesi gerekir. Örneğin, aşağıdaki sınıf bildirimleri bir hata oluşturur:

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- `partial` değiştirici yalnızca, `class`, `struct`veya `interface`anahtar kelimeleriyle hemen önce yer alabilir.

- İç içe geçmiş kısmi türlere, aşağıdaki örnekte gösterildiği gibi kısmi tür tanımlarında izin verilir:

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- Aynı türde parçalar olması gereken tüm kısmi tür tanımlarının aynı derlemede ve aynı modülde (. exe veya. dll dosyası) tanımlanması gerekir. Kısmi tanımlar birden çok modüle yayılamaz.

- Sınıf adı ve genel tür parametreleri tüm kısmi tür tanımlarında eşleşmelidir. Genel türler kısmi olabilir. Her kısmi bildirimin aynı parametre adlarını aynı sırada kullanması gerekir.

- Kısmi tür tanımında aşağıdaki anahtar sözcükler isteğe bağlıdır, ancak bir kısmi tür tanımında varsa, aynı türde başka bir kısmi tanımda belirtilen anahtar sözcüklerle çakışamaz:

  - [public](../../language-reference/keywords/public.md)

  - [private](../../language-reference/keywords/private.md)

  - [protected](../../language-reference/keywords/protected.md)

  - [internal](../../language-reference/keywords/internal.md)

  - [abstract](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - taban sınıfı

  - [Yeni](../../language-reference/keywords/new-modifier.md) değiştirici (iç içe yerleştirilmiş parçalar)

  - genel kısıtlamalar

Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../generics/constraints-on-type-parameters.md).

## <a name="example-1"></a>Örnek 1

### <a name="description"></a>Açıklama

Aşağıdaki örnekte, `Coords`sınıfının alanları ve Oluşturucusu tek bir kısmi sınıf tanımında ve `PrintCoords`üyesi başka bir kısmi sınıf tanımında bildirilmiştir.

### <a name="code"></a>Kod

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a>Örnek 2

### <a name="description"></a>Açıklama

Aşağıdaki örnek ayrıca kısmi yapılar ve arabirimler geliştirebileceğinizi gösterir.

### <a name="code"></a>Kod

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a>Kısmi Yöntemler

Kısmi bir sınıf veya yapı, kısmi bir yöntem içerebilir. Sınıfın bir kısmı metodun imzasını içerir. İsteğe bağlı bir uygulama aynı bölümde veya başka bir bölümde tanımlanabilir. Uygulama sağlanmazsa, yöntemi ve yöntemine yapılan tüm çağrılar derleme sırasında kaldırılır.

Kısmi Yöntemler, bir olaya benzer bir yöntemi tanımlamak için bir sınıfın bir parçasının Uygulayıcısı sağlar. Sınıfının diğer bölümünün uygulayıcısı, yöntemi uygulayıp uygulamamaya karar verebilir. Yöntem uygulanmadığından, derleyici yöntem imzasını ve yönteme yapılan tüm çağrıları kaldırır. Çağrılardaki bağımsız değişkenlerin değerlendirmesinden kaynaklanan sonuçlar da dahil olmak üzere yöntemine yapılan çağrılar, çalışma zamanında hiçbir etkiye sahip değildir. Bu nedenle, kısmi sınıftaki herhangi bir kod, uygulama sağlanmasa bile, kısmi bir yöntemi serbestçe kullanabilir. Yöntem çağrılırsa ancak uygulanmadığında, derleme zamanı veya çalışma zamanı hataları ortaya alınmaz.

Kısmi Yöntemler özellikle oluşturulan kodu özelleştirmenin bir yolu olarak faydalıdır. Bir yöntem adının ve imzasının ayrılmaya izin verir, böylece oluşturulan kod yöntemi çağırabilir, ancak geliştirici yöntemin uygulanıp uygulamamaya karar verebilir. Kısmi sınıflara çok benzeyen kısmi Yöntemler, bir kod üreticisi tarafından oluşturulan kodu ve bir insan geliştiricisi tarafından oluşturulan kodu, çalışma zamanı maliyetleri olmadan birlikte çalışmak üzere etkinleştirir.

Kısmi yöntem bildirimi iki bölümden oluşur: tanım ve uygulama. Bunlar kısmi bir sınıfın ayrı bölümlerinde veya aynı bölümde olabilir. Uygulama bildirimi yoksa, derleyici hem tanımlama bildirimini hem de yönteme yapılan tüm çağrıları en iyi duruma getirir.

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- Kısmi yöntem bildirimleri, bağlamsal anahtar sözcüğüyle [kısmen](../../language-reference/keywords/partial-type.md) başlamalı ve yöntemin [void](../../language-reference/keywords/void.md)döndürmesi gerekir.

- Kısmi yöntemlerin [içinde](../../language-reference/keywords/in-parameter-modifier.md) veya [ref](../../language-reference/keywords/ref.md) , ancak [Out](../../language-reference/keywords/out-parameter-modifier.md) parametreleri olabilir.

- Kısmi Yöntemler örtük olarak [özeldir](../../language-reference/keywords/private.md)ve bu nedenle [sanal](../../language-reference/keywords/virtual.md)olamaz.

- Gövde varlığı, tanımlama veya uygulama yapılıp yapılmayacağını belirlerse, kısmi Yöntemler [extern](../../language-reference/keywords/extern.md)olamaz.

- Kısmi yöntemlerin [statik](../../language-reference/keywords/static.md) ve [güvenli olmayan](../../language-reference/keywords/unsafe.md) değiştiriciler olabilir.

- Kısmi yöntemler genel olabilir. Kısıtlamalar, tanımlayıcı kısmi Yöntem bildirimine konur ve isteğe bağlı olarak uygulama bir tane üzerinde yinelenebilir. Parametre ve tür parametre adları, uygulama bildiriminde, tanımlanmasıyla aynı olmak zorunda değildir.

- Tanımlanmış ve uygulanmış, ancak yalnızca tanımlanmış kısmi bir yönteme değil kısmi bir yönteme [temsilci](../../language-reference/builtin-types/reference-types.md) oluşturabilirsiniz.

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [kısmi türler](~/_csharplang/spec/classes.md#partial-types) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar](./classes.md)
- [Yapılar](./structs.md)
- [Arabirimler](../interfaces/index.md)
- [partial (Tür)](../../language-reference/keywords/partial-type.md)
