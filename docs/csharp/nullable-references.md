---
title: Boş değer atanabilir başvuru türleri
description: Bu makalede eklenen boş değer atanabilir başvuru türleri, genel bir bakış sağlanmaktadır C# 8. Özellik null başvuru özel durumlar, yeni ve mevcut projeler için karşı güvenliği nasıl sağladığını öğreneceksiniz.
ms.date: 02/19/2019
ms.openlocfilehash: ac19cbba0e078af34801231145ee339d6e42a42b
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195918"
---
# <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

C#8.0 tanıtır **null başvuru türleri** ve **atanamayan başvuru türleri** önemli deyimleri hakkında başvuru türü değişkenler özelliklerini yapmanızı sağlayan:

- **Başvuru null olması beklenen değil**. Değişkenleri null kullanılmaması, derleyici bu değişkenleri ilk olmadan başvuru güvenli olduğundan emin olun kuralları zorlar. null olmayan denetleniyor:
  - Değişken için bir null olmayan değer başlatılmalıdır.
  - Değişken değeri hiçbir zaman atanabilir `null`.
- **Başvuru null**. Değişkenleri null olabilir, derleyici bir null başvuru için doğru denetlediyseniz emin olmak için farklı kuralları zorlar.
  - Değer null değil derleyici garanti edebilir, değişken yalnızca başvurusu kaldırılabilir.
  - Bu değişkenler varsayılan başlatılması `null` değeri ve değer atanabilir `null` diğer kod.

Bu yeni özellik, önceki sürümlerinde başvuru değişkenleri işlenmesi üzerinden önemli avantajlar sağlar. C# tasarım amacı uygulanamadı belirlendiği değişken bildirimi. Derleyici, başvuru türleri için null başvuru özel durumları karşı güvenliği sağlamadı:

- **Bir başvuru null olabilir**. Bir başvuru türü null'a veya daha sonra null olarak atanan uyarı verilir.
- **Başvuru null değil olarak kabul edilir**. Derleyici, başvuru türleri başvurusu kaldırıldığında tüm uyarılar sorun değil. (Null olabilir bir değişken başvuru olduğunda boş değer atanabilir başvurularla derleyici uyarıları verir).

Null başvuru türleri'nın eklenmesiyle, amacınız daha net bir şekilde bildirebilirsiniz. `null` Doğru şekilde temsil eden bir değişken değerine başvurmadığından değerdir. Tümünü kaldırmak için bu özelliği kullanmayın `null` kodunuzdan değerleri. Bunun yerine, derleyici ve kodunuzu okuyan diğer geliştiriciler için amacınız bildirmeniz gerekir. Amacınız bildirerek, derleyici, bu amacı ile tutarsız kod yazdığınızda bildirir.

A **boş değer atanabilir bir başvuru türü** aynı söz dizimini kullanarak belirtilen [boş değer atanabilen değer türleri](programming-guide/nullable-types/index.md): bir `?` değişkenin türüne eklenir. Örneğin, bir null olabilen bir dize değişkeni aşağıdaki değişken bildirimini temsil eden `name`:

```csharp
string? name;
```

Herhangi bir değişken burada `?` değil eklenir adı türüdür bir **NULL olmayan bir başvuru türü**. Bu özellik etkinleştirildiğinde, varolan kodda tüm başvuru türü değişkenler içerir.

Derleyici statik analiz, null olmayan değer için boş değer atanabilir bir başvuru biliniyorsa belirlemek için kullanır. Null olabilir, boş değer atanabilir bir başvuru başvuru varsa derleyici sizi uyarır. Kullanarak bu davranışı geçersiz kılabilirsiniz **null forgiving işleci** (`!`) izleyen bir değişken adı. Örneğin, biliyorsanız `name` değişken null değil ancak derleyici bir uyarı verir, derleyicinin analiz geçersiz kılmak için aşağıdaki kodu yazabilirsiniz:

```csharp
name!.Length;
```

Bu işleci hakkında ayrıntıları edinebilirsiniz [Taslak null başvuru türleri](../../_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) github'da belirtimi teklifi.

## <a name="nullability-of-types"></a>Null değer alabilme durumunun türleri

Herhangi bir başvuru türü'nın dört birine sahip *nullabilities*, uyarılar oluşturulduğunda açıklar:

- *Nonnullable*: Bu türün değişkenlerine null atanamaz. Bu tür değişkenler referanstan null işaretli olması gerekmez.
- *Boş değer atanabilir*: Bu türün değişkenlerine null atanabilir. İlk denetlemeden bu tür değişkenleri başvuruluyor `null` bir uyarısına neden olur.
- *Oblivious*: Bu ön,C# 8 durumu. Bu tür bir değişken başvurusu veya uyarılar olmadan atanmış.
- *Bilinmeyen*: Bu, genellikle tür parametreleri için kısıtlamalar derleyicinin tür olmalıdır nerede söyleme *boş değer atanabilir* veya *nonnullable*.

Öğesinin bir değişken bildirimi bir tür tarafından denetlenir *boş değer atanabilir bağlam* değişkenin bildirildiği içinde.

## <a name="nullable-contexts"></a>Boş değer atanabilir bağlamları

Boş değer atanabilir bağlamları derleyici başvuru türü değişkenler yorumlaması için ayrıntılı denetim olanağı. **Boş değer atanabilir bir ek açıklama bağlam** herhangi belirli kaynağını çizgidir `enabled` veya `disabled`. Öncesi düşünebilirsinizC# tüm kodunuzda derleme olarak 8 derleyici bir `disabled` boş değer atanabilir Bağlam: Herhangi bir başvuru türü null olabilir. **Boş değer atanabilir uyarı bağlamı** ayarlanabilir `enabled`, `disabled`, veya `safeonly`. Boş değer atanabilir uyarı bağlamı, akış Analizi ile derleyici tarafından oluşturulan uyarıların belirtir.

Boş değer atanabilir ek bağlam ve boş değer atanabilir uyarı bağlamı için bir proje kullanarak ayarlanabilir `Nullable` öğesinde, `csproj` dosya. Bu öğe, derleyicinin tür öğesinin nasıl yorumlayacağını ve hangi uyarıların oluşturulan yapılandırır. Geçerli ayarlar şunlardır:

- `enable`: Boş değer atanabilir bir ek açıklama bağlam **etkin**. Boş değer atanabilir uyarı bağlamı **etkin**.
  - Bir başvuru türü değişkenler `string` örneğin atanamayan yararlanabilirsiniz.  Tüm öğesinin uyarıları etkinleştirildi.
- `disable`: Boş değer atanabilir bir ek açıklama bağlam **devre dışı**. Boş değer atanabilir uyarı bağlamı **devre dışı**.
  - Bir başvuru türü değişkenler yalnızca önceki sürümleri gibi oblivious C#. Öğesinin tüm uyarıları devre dışı bırakıldı.
- `safeonly`: Boş değer atanabilir bir ek açıklama bağlam **etkin**. Boş değer atanabilir uyarı bağlamı **safeonly**.
  - Bir başvuru türü değişkenler nonnullable ' dir. Tüm güvenlik öğesinin uyarıları etkinleştirildi.
- `warnings`: Boş değer atanabilir bir ek açıklama bağlam **devre dışı**. Boş değer atanabilir uyarı bağlamı **etkin**.
  - Bir başvuru türü değişkenler oblivious. Tüm öğesinin uyarıları etkinleştirildi.
- `safeonlywarnings`: Boş değer atanabilir bir ek açıklama bağlam **devre dışı**. Boş değer atanabilir uyarı bağlamı **safeonly**.
  - Bir başvuru türü değişkenler oblivious. Tüm güvenlik öğesinin uyarıları etkinleştirildi.

> [!IMPORTANT]
> `Nullable` Öğe daha önce adlandırılmıştı `NullableContextOptions`. 16,2 p1, Visual Studio 2019 birlikte yeniden adlandırma verilir. .NET Core SDK'sı 3.0.100-preview5-011568 bu değişiklik yok. .NET Core CLI'yı kullanıyorsanız, kullanmanız gerekecektir `NullableContextOptions` kadar sonraki Önizleme kullanılabilir.

Bu aynı bağlamları projenizde her yerde ayarlamak için yönergeleri de kullanabilirsiniz:

- `#nullable enable`: Boş değer atanabilir uyarı bağlamına ve boş değer atanabilir bir ek açıklamanın bağlamı ayarlar **etkin**.
- `#nullable disable`: Boş değer atanabilir uyarı bağlamına ve boş değer atanabilir bir ek açıklamanın bağlamı ayarlar **devre dışı**.
- `#nullable safeonly`: Boş değer atanabilir bir ek açıklama içerik kümesine **etkin**ve uyarı bağlamına **safeonly**.
- `#nullable restore`: Uyarı bağlamı null ve boş değer atanabilir bir ek açıklama bağlam proje ayarlarına geri yükler.
- `#pragma warning disable nullable`: Boş değer atanabilir uyarı bağlamı kümesine **devre dışı**.
- `#pragma warning enable nullable`: Boş değer atanabilir uyarı bağlamı kümesine **etkin**.
- `#pragma warning restore nullable`: Boş değer atanabilir uyarı bağlamı proje ayarlarına geri yükler.
- `#pragma warning safeonly nullable`: Boş değer atanabilir uyarı bağlamı ayarlar **safeonly**.

Varsayılan boş değer atanabilir ek açıklaması ve uyarı bağlamı `disabled`. Bu karar, mevcut kod değişiklikleri ve yeni bir uyarı olmadan derlediğinden anlamına gelir.

Arasındaki farklar `enabled` ve `safeonly` boş değer atanabilir uyarı bağlamı null olmayan bir başvuru null başvuru atamak için uyarıları olan. Aşağıdaki atama bir uyarı oluşturur. bir `enabled` uyarı bağlamı, ancak bir `safeonly` uyarı bağlamı. Ancak, ikinci satırın nereye `s` referans edildi, bir uyarı üretir bir `safeonly` Bağlam:

```csharp
string s = null; // warning when nullable warning context is enabled.
var txt = s.ToString(); // warning when nullable warnings context is safeonly, or enabled.
```

### <a name="nullable-annotation-context"></a>Boş değer atanabilir bir ek açıklamanın bağlamı

Derleyici, bir boş değer atanabilir devre dışı bırakılmış ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Boş değer atanabilir başvuruları devre dışı bırakılmış bir bağlamda bildiremezsiniz.
- Tüm başvuru değişkenleri null atanabilir.
- Başvuru türünde bir değişken başvurusu kaldırıldığında uyarı üretilir.
- Devre dışı bırakılmış bir bağlamda null forgiving işleci kullanılamaz.

Davranış önceki sürümleri aynıdır C#.

Derleyici, bir boş değer atanabilir etkin ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Herhangi bir değişken başvuru türünde bir **atanamayan başvuru**.
- Herhangi bir değer atanamayan başvurusu güvenli bir şekilde başvurusu kaldırılabilir.
- Herhangi bir boş değer atanabilir bir başvuru türü (tarafından belirtildiği `?` Değişken bildiriminde türden sonra) null olabilir. Statik analiz değeri, başvurusu kaldırıldığında, null olmayan değer biliniyorsa belirler. Aksi halde, derleyici sizi uyarır.
- Null forgiving işleci, bir null başvuru null olmadığını bildirmek için kullanabilirsiniz.

Bir boş değer atanabilir etkin ek açıklama bağlamındaki `?` bir başvuru türü için eklenen karakter bildirir bir **boş değer atanabilir bir başvuru türü**. **Null forgiveness işleci** (`!`) ifade null olmadığını bildirmek için bir ifade eklenebilir.

## <a name="nullable-warning-context"></a>Boş değer atanabilir uyarı bağlamı

Boş değer atanabilir uyarı bağlamı null yapılabilir bir ek açıklama bağlamdan farklıdır. Yeni ek açıklamaların bile devre dışı bırakıldığında uyarılar etkin hale getirilebilir. Derleyici statik akış analizi belirlemek için kullanır. **null durumu** herhangi bir başvuru. Null ya da durumudur **değil null** veya **belki de null** olduğunda *boş değer atanabilir uyarı bağlamı* değil **devre dışı**. Derleyici bunun belirlendiğinde bir başvuru başvuru değilse **belki de null**, derleyici sizi uyarır. Bir başvuru durumu **belki de null** sürece derleyici iki koşullardan birini belirleyebilirsiniz:

1. Değişken kesinlikle bir null olmayan değere atandı.
1. Değişkenin veya ifadenin null karşı XML'deki başvurmadan önce iade edilmiş.

Bir değişkenin veya ifadenin başvuru her derleyici uyarıları oluşturur. bir **belki de null** boş değer atanabilir uyarı bağlamı olduğunda durumu `enabled` veya `safeonly`. Ayrıca, uyarılar oluşturulur, bir **belki de null** değişkenin veya ifadenin atandığı nonnullable başvuru türüne boş değer atanabilir bir ek açıklamanın bağlamı olduğunda `enabled`.

## <a name="learn-more"></a>Daha fazla bilgi edinin

- [Taslak null başvuru belirtimi](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Boş değer atanabilir başvuruları öğreticiye giriş](tutorials/nullable-reference-types.md)
- [Var olan bir geçiş için boş değer atanabilir başvuruları kod tabanı](tutorials/upgrade-to-nullable-references.md)
