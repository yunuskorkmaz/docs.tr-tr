---
title: İçinde desteklenen koleksiyon türleri System.Text.Json
description: Ad alanındaki API 'Ler tarafından serileştirme için hangi koleksiyon türlerinin desteklendiğini öğrenin System.Text.Json .
ms.date: 01/06/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 48033689e844dd29c999395255b5a1565fa2996e
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970995"
---
# <a name="supported-collection-types-in-no-locsystemtextjson"></a>İçinde desteklenen koleksiyon türleri System.Text.Json

Bu makale serileştirme ve seri durumundan çıkarma için hangi koleksiyonların desteklendiği hakkında genel bakış sunar. <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> , serileştirme için bir koleksiyon türünü destekler:

* Türetiliyor <xref:System.Collections.IEnumerable> .
* Seri hale getirilebilir öğeleri içerir.

Seri hale getirici <xref:System.Collections.IEnumerable.GetEnumerator> yöntemini çağırır ve öğeleri yazar.

Seri durumdan çıkarma daha karmaşıktır ve bazı koleksiyon türleri için desteklenmez.

Aşağıdaki bölümler ad alanına göre düzenlenmiştir ve serileştirme ve seri durumdan çıkarma için hangi türlerin desteklendiğini gösterir.

## <a name="systemcollections-namespace"></a>System. Collections ad alanı

| Tür                                      | Serileştirme | Seri |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | ✔️           | ✔️              |
| <xref:System.Collections.BitArray>        | ✔️           | ❌              |
| <xref:System.Collections.DictionaryEntry> | ✔️           | ✔️              |
| <xref:System.Collections.Hashtable>       | ✔️           | ✔️              |
| <xref:System.Collections.Queue>           | ✔️           | ✔️              |
| <xref:System.Collections.SortedList>      | ✔️           | ✔️              |
| <xref:System.Collections.Stack>           | ✔️           | ✔️              |
| <xref:System.Collections.ICollection>     | ✔️           | ✔️              |
| <xref:System.Collections.IDictionary>     | ✔️           | ✔️              |
| <xref:System.Collections.IEnumerable>     | ✔️           | ✔️              |
| <xref:System.Collections.IList>           | ✔️           | ✔️              |

## <a name="systemcollectionsgeneric-namespace"></a>System. Collections. Generic ad alanı

::: zone pivot="dotnet-5-0"

| Tür                                                      | Serileştirme | Seri |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Generic.Dictionary%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedDictionary%602> \* | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedList%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IDictionary%602> \*      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyDictionary%602> \* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Tür                                                                                            | Serileştirme | Seri |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [Sözlük \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>                                                     | ✔️           | ✔️              |
| [SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*    | ✔️           | ✔️              |
| [SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | ✔️           | ✔️              |
| [IDictionary \<string, TValue> ](xref:System.Collections.Generic.IDictionary%602)\*              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | ✔️           | ✔️              |
| [IReadOnlyDictionary \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                                                      | ✔️           | ✔️              |

::: zone-end

\* Bkz. [desteklenen anahtar türleri](#supported-key-types).

## <a name="systemcollectionsimmutable-namespace"></a>System. Collections. sabit ad alanı

::: zone pivot="dotnet-5-0"

| Tür                                                              | Serileştirme | Seri |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*  | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableDictionary%602> \*\* | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*        | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Tür                                                                                                          | Serileştirme | Seri |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | ✔️           | ✔️              |
| [ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | ✔️           | ✔️              |
| [ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*| ✔️       | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*                                                     | ✔️           | ✔️              |
| [IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*                                                    | ✔️           | ✔️              |

::: zone-end

\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).

\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).

## <a name="systemcollectionsspecialized-namespace"></a>System. Collections. özelleşmiş ad alanı

| Tür                                                      | Serileştirme | Seri |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | ✔️           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | ✔️           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.StringCollection>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | ✔️           | ❌              |

\*<xref:System.Collections.Specialized.BitVector32>Seri durumdan kaldırıldığında, <xref:System.Collections.Specialized.BitVector32.Data> özelliği ortak bir ayarlayıcısı olmadığından atlanır. Özel durum oluşturulmaz.

## <a name="systemcollectionsconcurrent-namespace"></a>System. Collections. eşzamanlı ad alanı

::: zone pivot="dotnet-5-0"

| Tür                                                          | Serileştirme | Seri |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \*   | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Tür                                                        | Serileştirme | Seri |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | ✔️           | ❌              |
| [ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\* |✔️|✔️|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \* | ✔️           | ✔️              |

::: zone-end

\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).

\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).

## <a name="systemcollectionsobjectmodel-namespace"></a>System. Collections. ObjectModel Ad alanı

::: zone pivot="dotnet-5-0"

| Tür                                                           | Serileştirme | Seri |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | ✔️    | ❌             |

\* Anahtarlar olmayanlar `string` desteklenmez.

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Tür                                                           | Serileştirme | Seri |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| [ReadOnlyDictionary \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| ✔️     | ❌             |

\* Bkz. [desteklenen anahtar türleri](#supported-key-types).

::: zone-end

## <a name="custom-collections"></a>Özel koleksiyonlar

Önceki ad alanlarından birinde olmayan herhangi bir koleksiyon türü özel bir koleksiyon olarak kabul edilir. Bu tür türler, ASP.NET Core tarafından tanımlanan Kullanıcı tanımlı türleri ve türleri içerir. Örneğin, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> Bu grupta bulunur.

Tüm özel koleksiyonlar (türetilen her şey `IEnumerable` ), öğe türleri desteklendiği sürece serileştirme için desteklenir.

### <a name="custom-collections-with-deserialization-support"></a>Seri durumdan çıkarma desteği olan özel koleksiyonlar

Özel bir koleksiyon, seri durumdan çıkarma için desteklenir:

::: zone pivot="dotnet-5-0"

* Bir arabirim veya Özet değil.
* Parametresiz oluşturucusu vardır.
* Tarafından desteklenen öğe türlerini içerir <xref:System.Text.Json.JsonSerializer> .
* Aşağıdaki arabirimlerden veya sınıflardan birini veya daha fazlasını uygular veya devralır:
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <xref:System.Collections.Generic.IDictionary%602> \*\*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

::: zone pivot="dotnet-core-3-1"

* Bir arabirim veya Özet değil.
* Parametresiz oluşturucusu vardır.
* Tarafından desteklenen öğe türlerini içerir <xref:System.Text.Json.JsonSerializer> .
* Aşağıdaki arabirimlerden veya sınıflardan birini veya daha fazlasını uygular veya devralır:
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * [IDictionary \<string, TValue> ](xref:System.Collections.Generic.IDictionary%602)\*\*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

  \*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).

  \*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).

### <a name="custom-collections-with-known-issues"></a>Bilinen sorunları olan özel koleksiyonlar

Aşağıdaki özel koleksiyonlarla ilgili bilinen sorunlar vardır:

- <xref:System.Dynamic.ExpandoObject>: Bkz. [DotNet/Runtime # 29690](https://github.com/dotnet/runtime/issues/29690).
- <xref:System.Dynamic.DynamicObject>: Bkz. [DotNet/Runtime # 1808](https://github.com/dotnet/runtime/issues/1808).
- <xref:System.Data.DataTable>: Bkz. [DotNet/docs # 21366](https://github.com/dotnet/docs/issues/21366).
- <xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: Bkz. [DotNet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).
- <xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: Bkz. [DotNet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).

Bilinen sorunlar hakkında daha fazla bilgi için [ System.Text.Json içindeki açık sorunlar ](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)bölümüne bakın.

## <a name="supported-key-types"></a>Desteklenen anahtar türleri

::: zone pivot="dotnet-5-0"

Anahtarlar ve türleri için desteklenen türler `Dictionary` `SortedList` şunlardır:

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* `Object` (Yalnızca serileştirme ve çalışma zamanı türü bu listede desteklenen türlerden biri ise.)
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

\*\*`string`Anahtarlar `Dictionary` ve `SortedList` türler .NET Core 3,1 ' de desteklenmez.

::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JsonSerializerOptions örneklerinin örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harf duyarlı eşlemeyi etkinleştirme](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksayma](system-text-json-ignore-properties.md)
* [Geçersiz JSON’a izin verme](system-text-json-invalid-json.md)
* [Sap taşması JSON’ı](system-text-json-handle-overflow.md)
* [Başvuruları koruma](system-text-json-preserve-references.md)
* [Sabit türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [Üzerinde Newtonsoft.Jsgeçir System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Karakter kodlamasını özelleştirme](system-text-json-character-encoding.md)
* [Özel serileştiriciler ve seri hale getiriciler yazma](write-custom-serializer-deserializer.md)
* [JSON serileştirme için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
