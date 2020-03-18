---
title: Boş değer atanabilir başvuru türleri
description: Bu makale, C# 8.0'a eklenen geçersiz başvuru türlerine genel bir bakış sağlar. Yeni ve varolan projeler için özelliğin geçersiz başvuru özel durumlarına karşı güvenliği nasıl sağladığını öğreneceksiniz.
ms.technology: csharp-null-safety
ms.date: 02/19/2019
ms.openlocfilehash: bb4c2b6951a38eeb705c7de50ef5d9645350e336
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399429"
---
# <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

C# 8.0, başvuru türü değişkenlerinin özellikleri hakkında önemli ifadeler yapmanızı sağlayan **nullable referans türleri** ve **nullable olmayan başvuru türleri** sunar:

- **Bir başvurunun null olması gerekmez.** Değişkenlerin null olması gerekmediği zaman, derleyici bu değişkenlerin null olup olmadığını kontrol etmeden bu değişkenleri dereference'ın güvenli olduğundan emin olan kurallar uygular:
  - Değişken null olmayan bir değere başlatılmalıdır.
  - Değişkene hiçbir zaman değer `null`atanamaz.
- **Bir başvuru geçersiz olabilir.** Değişkenler null olabilir, derleyici doğru bir null başvuru için kontrol emin olmak için farklı kurallar uygular:
  - Değişken yalnızca derleyici değerin null olmadığını garanti edebildiği zaman başvurudan arındırılabilir.
  - Bu değişkenler varsayılan `null` değerle baş harflere para `null` biçilebilir ve diğer koddaki değer atanabilir.

Bu yeni özellik, tasarım amacının değişken bildiriminden belirlenemediği C#'nin önceki sürümlerinde referans değişkenlerinin işlenmesi üzerinde önemli faydalar sağlar. Derleyici, başvuru türleri için null başvuru özel durumlarına karşı güvenlik sağlamadı:

- **Bir başvuru null olabilir.** Bir başvuru türü null'a başharflediğinde veya daha sonra null atandığında hiçbir uyarı verilmez.
- **Bir başvurunun null olmadığı varsayılır.** Derleyici, başvuru türleri başvurudan çıktığında herhangi bir uyarı yayımlamıyor. (Nullable referansları ile derleyici, null olabilecek bir değişkeni dereference'ınız olduğunda uyarılar verir).

Nullable başvuru türlerinin eklenmesiyle, niyetinizi daha net bir şekilde bildirebilirsiniz. Değer, `null` bir değişkenin bir değere başvurmadığını temsil etmenin doğru yoludur. Bu özelliği kodunuzdaki tüm `null` değerleri kaldırmak için kullanmayın. Bunun yerine, amacınızı derleyiciye ve kodunuzu okuyan diğer geliştiricilere bildirmelisiniz. Derleyici, niyetinizi beyan ederek, bu niyetle tutarsız bir kod yazarken sizi bilgilendirir.

Nullable **başvuru türü nullable** [değer türleri](language-reference/builtin-types/nullable-value-types.md)ile aynı sözdizimi kullanılarak kaydedilir : a `?` değişkenin türüne eklenir. Örneğin, aşağıdaki değişken bildirimi nullable string `name`değişkeni temsil eder:

```csharp
string? name;
```

Tür adına `?` eklenemeyen herhangi bir **değişken, nullable olmayan**bir başvuru türüdür. Bu özelliği etkinleştirdiğinizde varolan koddaki tüm başvuru türü değişkenlerini içerir.

Derleyici, nullable bir başvurunun null olmayan olarak bilinip bilinmeyeceğini belirlemek için statik çözümleme kullanır. Derleyici, nullable bir başvuru geçersiz olabilir dereference sizi uyarır. Değişken bir adı izleyen [null-affgiving işleci](language-reference/operators/null-forgiving.md) `!` kullanarak bu davranışı geçersiz kılabilirsiniz. Örneğin, değişkenin `name` null olmadığını ancak derleyicinin bir uyarı yayınladığını biliyorsanız, derleyicinin çözümlemesi geçersiz kılmak için aşağıdaki kodu yazabilirsiniz:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Türlerin nullability

Herhangi bir başvuru türü, uyarılar oluşturulduğunda açıklayan dört *nullabilities*biri olabilir:

- *Nullable*: Null bu tür değişkenlere atanamaz. Bu tür değişkenlerin dereferencing önce null-checked gerekmez.
- *Nullable*: Null bu tür değişkenlere atanabilir. Bu tür değişkenleri ilk olarak denetlemeden `null` dereferencing bir uyarıya neden olur.
- *Habersiz*: Bu ön-C # 8.0 durumudur. Bu tür değişkenler dereferenced veya uyarı olmadan atanabilir.
- *Bilinmiyor*: Bu genellikle kısıtlamaların derleyiciye türün *nullable* veya *nullable*olması gerektiğini söylemediği tür parametreleri içindir.

Değişken bildirimindeki bir türün nullability değişken in beyan edildiği *nullable bağlam* tarafından denetlenir.

## <a name="nullable-contexts"></a>Nullable bağlamlar

Nullable bağlamlar derleyicinin başvuru türü değişkenlerini nasıl yorumladığına göre ince taneli denetim sağlar. Belirli bir kaynak satırının **geçersiz ek açıklama bağlamı** etkin veya devre dışı bırakılır. C öncesi 8.0 derleyicisini tüm kodunuzu devre dışı bırakılmış geçersiz bir bağlamda derleyen olarak düşünebilirsiniz: herhangi bir başvuru türü null olabilir. **Geçersiz uyarılar bağlamı** da etkinleştirilebilir veya devre dışı bırakılmış olabilir. Nullable uyarılar bağlamı, akış çözümlemesi kullanarak derleyici tarafından oluşturulan uyarıları belirtir.

`Nullable` *.csproj* dosyanızdaki öğeyi kullanarak bir proje için geçersiz ek açıklama bağlamı ve nullable uyarı bağlamı ayarlanabilir. Bu öğe, derleyicinin türlerin nullability nasıl yorumladığını ve hangi uyarıları oluşturulur yapılandırır. Geçerli ayarlar şunlardır:

- `enable`: Nullable ek açıklama bağlamı **etkinleştirilir.** Nullable uyarı bağlamı **etkindir.**
  - Örneğin, `string` bir başvuru türünün değişkenleri nullable değildir.  Tüm nullability uyarıları etkinleştirilir.
- `warnings`: Geçersiz ek açıklama bağlamı **devre dışı bırakılır.** Nullable uyarı bağlamı **etkindir.**
  - Başvuru türünün değişkenleri kayıtsız. Tüm nullability uyarıları etkinleştirilir.
- `annotations`: Nullable ek açıklama bağlamı **etkinleştirilir.** Nullable uyarı bağlamı **devre dışı bırakılır.**
  - Bir başvuru türünün değişkenleri, örneğin dize, nullable değildir. Tüm nullability uyarıları devre dışı bırakılır.
- `disable`: Geçersiz ek açıklama bağlamı **devre dışı bırakılır.** Nullable uyarı bağlamı **devre dışı bırakılır.**
  - Bir başvuru türünün değişkenleri, C#'ın önceki sürümlerinde olduğu gibi habersizdir. Tüm nullability uyarıları devre dışı bırakılır.

**Örnek**:

```xml
<Nullable>enable</Nullable>
```

Projenizin herhangi bir yerinde bu aynı bağlamları ayarlamak için yönergeler de kullanabilirsiniz:

- `#nullable enable`: **Nullable**ek açıklama bağlamını ve nullable warning bağlamını etkin olarak ayarlar.
- `#nullable disable`: Geçersiz kılınan ek açıklama bağlamını ve geçersiz uyarı bağlamını **devre dışı bırakılır.**
- `#nullable restore`: Proje ayarlarına geçersiz ek açıklama bağlamını ve nullable uyarı bağlamını geri yükler.
- `#nullable disable warnings`: Geçersiz **kılınan**uyarı bağlamını devre dışı bırakılmış olarak ayarlayın.
- `#nullable enable warnings`: Nullable uyarı bağlamını **etkin**olarak ayarlayın.
- `#nullable restore warnings`: Nullable uyarı bağlamını proje ayarlarına geri yükler.
- `#nullable disable annotations`: Geçersiz kılınan ek açıklama bağlamını **devre dışı bırakılmış**olarak ayarlayın.
- `#nullable enable annotations`: Nullable ek açıklama bağlamını **etkin**olarak ayarlayın.
- `#nullable restore annotations`: Ek açıklama uyarı bağlamını proje ayarlarına geri yükler.

Varsayılan olarak, geçersiz ek açıklama ve uyarı bağlamları **devre dışı bırakılır.** Bu, varolan kodunuzu değişiklik yapmadan ve yeni uyarılar oluşturmadan derletir anlamına gelir.

## <a name="nullable-annotation-context"></a>Nullable ek açıklama bağlamı

Derleyici devre dışı bırakılmış geçersiz ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Geçersiz kılınabilir başvuruları devre dışı bırakılmış bir bağlamda bildiremezsiniz.
- Tüm referans değişkenlerine null değeri atanabilir.
- Başvuru türünün değişkeni referanssız olduğunda hiçbir uyarı oluşturulmamaktadır.
- Null-affgiving işleci devre dışı bırakılmış bir bağlamda kullanılamaz.

Davranış, C#'ın önceki sürümleriyle aynıdır.

Derleyici, etkin leştirilmiş geçersiz ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Başvuru türünün herhangi bir değişkeni **nullable olmayan**bir başvurudur.
- Nullable olmayan herhangi bir referans güvenle dereferenced olabilir.
- Herhangi bir nullable referans `?` türü (değişken bildiriminde tür sonra kaydetti) null olabilir. Statik çözümleme, değerin referanssız olduğu zaman null'suz olarak bilinip bilinmeyeceğini belirler. Değilse, derleyici sizi uyarır.
- Null-affgiving işleci, geçersiz bir başvurunun null olmadığını bildirmek için kullanabilirsiniz.

Etkinleştirilmiş nullable ek açıklama bağlamında, başvuru türüne eklenen `?` karakter geçersiz bir başvuru **türü**bildirir. **Hükümsüz affedici işleç,** `!` ifadenin null olmadığını bildiren bir ifadeye eklenebilir.

## <a name="nullable-warning-context"></a>Nullable uyarı bağlamı

Geçersiz uyarı bağlamı, geçersiz ek açıklama bağlamından farklıdır. Yeni ek açıklamalar devre dışı bırakıldığında bile uyarılar etkinleştirilebilir. Derleyici, herhangi bir başvurunun **null durumunu** belirlemek için statik akış çözümlemesi kullanır. Null durumu, *nullable uyarı bağlamı* **devre dışı**bırakılmadığında ya null ya da **belki null** **değildir.** Derleyici **belki de null**olduğunu belirlediğinde bir referans ı salarsanız, derleyici sizi uyarır. Derleyici iki koşuldan birini belirleyemediği sürece başvurunun durumu **belki de null'dur:**

1. Değişken kesinlikle null olmayan bir değere atanmıştır.
1. Değişken veya ifade, başvurudan çıkmadan önce null'a karşı denetlenmiştir.

Derleyici, boşuyarı bağlamı etkinleştirildiğinde bir değişkeni veya ifadeyi **belki de null** durumunda dereference'ı yaptığınızda uyarılar oluşturur. Ayrıca, etkin nullable ek açıklama bağlamında nullable olmayan bir başvuru türüne **bir nullvariable** veya ifade atandığında uyarılar oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Taslak nullable referans türleri belirtimi](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Nullable referanslar öğretici giriş](tutorials/nullable-reference-types.md)
- [Varolan bir kod tabanını nullable başvurulara geçirin](tutorials/upgrade-to-nullable-references.md)
