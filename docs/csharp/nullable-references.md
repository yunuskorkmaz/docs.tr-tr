---
title: Null başvuru türleri
description: Bu makalede eklenen boş değer atanabilir başvuru türleri, genel bir bakış sağlanmaktadır C# 8. Özellik null başvuru özel durumlar, yeni ve mevcut projeler için karşı güvenliği nasıl sağladığını öğreneceksiniz.
ms.date: 12/03/2018
ms.openlocfilehash: f18fc9dbce2f934b216b3eb0b80658fec6b44c46
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156488"
---
# <a name="nullable-reference-types"></a>Null başvuru türleri

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

A **boş değer atanabilir bir başvuru türü** aynı söz dizimini kullanarak belirtilen [boş değer atanabilen değer türleri](programming-guide/nullable-types/index.md): bir `?` değişkenin türüne eklenir. Örneğin, bir null olabilen bir dize değişkeni aşağıdaki değişken bildirimini temsil eden `name`:

```csharp
string? name;
```

Herhangi bir değişken burada `?` değil eklenir adı türüdür bir **NULL olmayan bir başvuru türü**. Bu özellik etkinleştirildiğinde, varolan kodda tüm başvuru türü değişkenler içerir.

Derleyici statik analiz, null olmayan değer için boş değer atanabilir bir başvuru biliniyorsa belirlemek için kullanır. Null olabilir, boş değer atanabilir bir başvuru başvuru varsa derleyici sizi uyarır. Kullanarak bu davranışı geçersiz kılabilirsiniz **null forgiving işleci** (`!`) izleyen bir değişken adı. Örneğin, biliyorsanız `name` değişken null değil ancak derleyici bir uyarı verir, derleyicinin analiz geçersiz kılmak için aşağıdaki kodu yazabilirsiniz:

```csharp
name!.Length;
```

Bu işleci hakkında ayrıntıları edinebilirsiniz [Taslak null başvuru türleri](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md#the-null-forgiving-operator) github'da belirtimi teklifi.

## <a name="nullable-contexts"></a>Boş değer atanabilir bağlamları

Boş değer atanabilir bağlamları derleyici başvuru türü değişkenler yorumlaması için ayrıntılı denetim olanağı. Boş değer atanabilir bağlamı herhangi belirli kaynak satırı, `enabled` veya `disabled`. Öncesi düşünebilirsinizC# tüm kodunuzda derleme olarak 8 derleyici bir `disabled` boş değer atanabilir Bağlam: Herhangi bir başvuru türü null olabilir. Bir başvuru türü değişkenler başvurusu kaldırıldığında uyarı oluşturulmaz.

Boş değer atanabilir bağlamı, yeni bir pragma kullanılarak denetlenir:

- `#nullable enable` boş değer atanabilir bağlamının etkin ayarlar.
- `#nullable disable` boş değer atanabilir bağlam devre dışı olarak ayarlar.

Varsayılan null bağlam `disabled`. Bu karar, mevcut kod değişiklikleri ve yeni bir uyarı olmadan derlediğinden anlamına gelir.

Derleyici, devre dışı bırakılmış bir boş değer atanabilir bağlamında aşağıdaki kuralları kullanır:

- Boş değer atanabilir başvuruları devre dışı bırakılmış bir bağlamda bildiremezsiniz.
- Tüm başvuru değişkenleri null atanabilir.
- Başvuru türünde bir değişken başvurusu kaldırıldığında uyarı üretilir.
- Devre dışı bırakılmış bir bağlamda null forgiving işleci kullanılamaz.

Davranış önceki sürümleri aynıdır C#.

Derleyici, etkin bir boş değer atanabilir bağlamında aşağıdaki kuralları kullanır:

- Herhangi bir değişken başvuru türünde bir **atanamayan başvuru**.
- Herhangi bir değer atanamayan başvurusu güvenli bir şekilde başvurusu kaldırılabilir.
- Herhangi bir boş değer atanabilir bir başvuru türü (tarafından belirtildiği `?` Değişken bildiriminde türden sonra) null olabilir. Statik analiz değeri, başvurusu kaldırıldığında, null olmayan değer biliniyorsa belirler. Aksi halde, derleyici sizi uyarır.
- Null forgiving işleci, bir null başvuru null olmadığını bildirmek için kullanabilirsiniz.

Daha zengin bir dil bilgisi nullable bağlamlarını için önerilen ve gelecekteki önizlemelere kullanılabilir olacak. Boş değer atanabilir bağlamları hakkında daha fazla bilgi için bkz. [boş değer atanabilir başvurusu belirtiminin](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md#nullable-contexts) taslak.

## <a name="null-states-of-nullable-references"></a>Null başvuru null durumları

Derleyici statik analiz belirlemek için kullanır. **null durumu** herhangi bir null başvuru. Null ya da durumudur **değil null** veya **belki de null**. Derleyici bunun belirlendiğinde bir null başvuru başvuru varsa **belki de null**, derleyici sizi uyarır. Boş değer atanabilir bir başvuru durumu **belki de null** sürece derleyici iki koşullardan birini belirleyebilirsiniz:

1. Değişken kesinlikle bir null olmayan değere atandı.
1. Değişkeni null karşı XML'deki başvurmadan önce iade edildi.

NULL olmayan başvurular hiçbir zaman null değerine ayarlanırsa, derleyici zorlar. Bunları bir null olmayan değere başlatmanız gerekir. Aksi takdirde, NULL olmayan bir başvuru başlatılan değildi derleyici sizi uyarır. Boş değer atanabilir bir başvuru NULL olmayan bir başvuru atama her derleyici Ayrıca, sizi uyarır **null olabilir**. Yalnızca atayabilirsiniz boş değer atanabilir bir başvuru NULL olmayan bir başvuru, null başvuru ise gelir **değil null**.

## <a name="learn-more"></a>Daha fazla bilgi edinin

- [Taslak null başvuru belirtimi](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md)
- [Boş değer atanabilir başvuruları öğreticiye giriş](tutorials/nullable-reference-types.md)
