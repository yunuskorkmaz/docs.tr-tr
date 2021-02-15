---
title: Kod stili adlandırma kuralları
description: Kod öğelerinin adlandırılması için .NET kod stili kuralları hakkında bilgi edinin.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: df2cbc8299d853b5730bc39eb25c6f97b6575655
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429214"
---
# <a name="naming-rules"></a>Adlandırma kuralları

`.editorconfig`Dosyanızda sınıflar, Özellikler ve yöntemler gibi .NET programlama dil kodu öğelerinin nasıl adlandırılması gerektiğini belirten ve zorlayabileceğiniz **adlandırma kuralları** tanımlayabilirsiniz &mdash; &mdash; . Örneğin, genel üyelerin büyük harfle veya özel alanların ile başlaması gerektiğini belirtebilirsiniz `_` .

Adlandırma kuralında üç bileşen vardır:

* Kuralın geçerli olduğu **sembol grubu** , örneğin, Genel Üyeler veya özel alanlar.
* Kuralla ilişkilendirilecek **adlandırma stili** , örneğin, adın büyük harfli olması veya bir alt çizgiyle başlaması gerekir.
* Kuralı zorlamaya yönelik önem derecesi.

İlk olarak, sembol grubunu ve adlandırma stilini belirtmeniz ve bunların her birine bir başlık vermeniz gerekir. Ardından, her şeyi birbirine bağlayan adlandırma kuralını belirtirsiniz.

## <a name="general-syntax"></a>Genel sözdizimi

Adlandırma kuralı, sembol grubu veya adlandırma stili tanımlamak için aşağıdaki sözdizimini kullanarak bir veya daha fazla özellik ayarlayın:

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

Her özellik yalnızca bir kez ayarlanmalıdır, ancak bazı ayarlar birden fazla virgülle ayrılmış değere izin verir.

Özelliklerin sırası önemli değildir.

### \<kind>

**\<kind>** Hangi tür öğe tanımlandığını belirtir &mdash; adlandırma kuralı, sembol grubu veya adlandırma stili &mdash; ve aşağıdakilerden biri olmalıdır:

| Bir özelliği ayarlamak için | Değeri kullanın \<kind> | Örnek |
| --- | --- | -- |
| Adlandırma kuralı | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| Sembol grubu | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| Adlandırma stili | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

Her tanım &mdash; [adlandırma kuralı](#naming-rule-properties), [sembol grubu](#symbol-group-properties)veya [adlandırma stilinin](#naming-style-properties)her türü, &mdash; Aşağıdaki bölümlerde açıklandığı gibi kendi desteklenen özelliklerine sahiptir.

### \<title>

**\<title>** , birden çok özellik ayarını tek bir tanım halinde ilişkilendiğinde seçeceğiniz açıklayıcı bir addır. Örneğin, aşağıdaki özellikler iki sembol grubu tanımı üretir `interface` ve `types` her birinin üzerinde iki özelliği ayarlanmış olur.

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a>Adlandırma kuralı özellikleri

Kuralın etkili olması için tüm adlandırma kuralı özellikleri gereklidir.

| Özellik | Açıklama |
| -- | -- |
| `symbols` | Bir sembol grubunun başlığı; adlandırma kuralı bu gruptaki simgelere uygulanacak |
| `style` | Bu kuralla ilişkilendirilmesi gereken adlandırma stilinin başlığı |
| `severity` |  Adlandırma kuralını zorlayacağı önem derecesini ayarlar. İlişkili değeri kullanılabilir [önem düzeylerinden](../configuration-options.md#severity-level)birine ayarlayın. <sup>1</sup> |

**Notlar:**

1. Bir adlandırma kuralı içindeki önem derecesi yalnızca Visual Studio gibi geliştirme IDEs 'in içinde olur. Bu ayar C# veya VB derleyicileri tarafından anlaşılmaz, bu nedenle derleme sırasında dikkate verilmez. Derleme üzerinde adlandırma stili kuralları zorlamak için, bunun yerine [kod kuralı önem derecesi yapılandırmasını](#rule-id-ide1006-naming-rule-violation)kullanarak önem derecesi ayarlamanız gerekir. Daha fazla bilgi için bu [GitHub sorununa](https://github.com/dotnet/roslyn/issues/44201)bakın.

## <a name="symbol-group-properties"></a>Sembol grubu özellikleri

Hangi simgelerin gruba ekleneceğini sınırlamak için sembol grupları için aşağıdaki özellikleri ayarlayabilirsiniz. Tek bir özellik için birden çok değer belirtmek için değerleri virgülle ayırın.

| Özellik | Açıklama | İzin verilen değerler | Gerekli |
| -- | -- | -- | -- |
| `applicable_kinds` | Grup <sup>1</sup> ' deki sembol türleri | `*` (tüm sembolleri belirtmek için bu değeri kullanın)<br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | Yes |
| `applicable_accessibilities` | Gruptaki sembollerin erişilebilirlik düzeyleri | `*` (tüm erişilebilirlik düzeylerini belirtmek için bu değeri kullanın)<br/>`public`<br/>`internal` veya `friend`<br/>`private`<br/>`protected`<br/>`protected_internal` veya `protected_friend`<br/>`private_protected`<br/>`local` (bir yöntem içinde tanımlanan semboller için) | Yes |
| `required_modifiers` | Yalnızca _Tüm_ belirtilen değiştiricilere sahip sembolleri Eşleştir <sup>2</sup> | `abstract` veya `must_inherit`<br/>`async`<br/>`const`<br/>`readonly`<br/>`static` veya `shared` <sup>3</sup> | No |

**Notlar:**

1. Demet üyeleri şu anda sürümünde desteklenmemektedir `applicable_kinds` .
2. Sembol grubu, özelliğindeki _Tüm_ değiştiricilerin eşleşir `required_modifiers` .  Bu özelliği atlarsanız, eşleşme için belirli bir değiştirici gerekmez. Bu, sembolün değiştiricilerin bu kuralın uygulanıp uygulanmadığı üzerinde hiçbir etkisi olmayacağı anlamına gelir.
3. Grubunuz `static` özelliğinde veya özelliğine sahipse `shared` `required_modifiers` , gruplar örtülü olduklarından, semboller de içerecektir `const` `static` / `Shared` . Ancak, `static` adlandırma kuralının semboller için uygulanmasını istemiyorsanız `const` sembol grubu ile yeni bir adlandırma kuralı oluşturabilirsiniz `const` .

## <a name="naming-style-properties"></a>Adlandırma stili özellikleri

Adlandırma stili, kuralla zorlamak istediğiniz kuralları tanımlar. Örneğin:

* Büyük harfe çevir `PascalCase`
* İle başlar `m_`
* Şununla biter `_g`
* Sözcükleri ile ayır `__`

Adlandırma stili için aşağıdaki özellikleri ayarlayabilirsiniz:

| Özellik | Açıklama | İzin verilen değerler | Gerekli |
| -- | -- | -- | -- |
| `capitalization` | Sembol içindeki sözcüklerin büyük küçük harf stili | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | Evet<sup>1</sup> |
| `required_prefix` | Bu karakterlerle başlaması gerekir | | No |
| `required_suffix` | Bu karakterlerle bitmelidir | | No |
| `word_separator` | Simgenin içindeki sözcüklerin bu karakterle ayrılması gerekir | | No |

**Notlar:**

1. Adlandırma stiliniz kapsamında bir büyük harf stili belirtmeniz gerekir, aksi takdirde adlandırma stiliniz yok sayılabilir.

## <a name="rule-order"></a>Kural sırası

Adlandırma kurallarının bir EditorConfig dosyasında tanımlandığı sıra bu şekilde değildir. Adlandırma kuralları kuralların tanımına göre otomatik olarak sıralanır. [Editorconfig dil hizmeti uzantısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) , bir editorconfig dosyasını çözümleyebilir ve dosyadaki kural sıralaması derleyicinin çalışma zamanında kullandıklarıyla farklı olduğunda rapor durumlarını rapor edebilir.

> [!NOTE]
>
> Visual Studio 'nun Visual Studio 2019 sürüm 16,2 ' den önceki bir sürümünü kullanıyorsanız, adlandırma kuralları, EditorConfig dosyasında en çok belirli olan en az özel olarak sıralanmalıdır. Uygulanabilecek ilk kural, uygulanan tek kuraldır. Ancak, aynı ada sahip birden fazla kural *özelliği* varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır. Daha fazla bilgi için bkz. [Dosya hiyerarşisi ve önceliği](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).

## <a name="default-naming-styles"></a>Varsayılan adlandırma stilleri

Herhangi bir özel adlandırma kuralı belirtmezseniz, aşağıdaki varsayılan stiller kullanılır:

- ,,, Veya erişilebilirlik ile sınıflar, yapılar, numaralandırmalar, Özellikler ve olaylar için `public` `private` `internal` `protected` `protected_internal` varsayılan adlandırma stili, Pascal durumdur.

- ,,, `public` Veya erişilebilirliği olan arabirimler için `private` `internal` `protected` `protected_internal` , varsayılan adlandırma stili, gerekli bir **I** ön eki olan Pascal durumdur.

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a>Kod kuralı KIMLIĞI: `IDE1006 (Naming rule violation)`

Tüm adlandırma seçeneklerinin kural KIMLIĞI `IDE1006` ve başlığı vardır `Naming rule violation` . Aşağıdaki söz dizimine sahip bir EditorConfig dosyasında genel olarak adlandırma ihlallerinin önem derecesini yapılandırabilirsiniz:

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

Önem derecesi değeri, `warning` `error` [derleme üzerinde zorlanmalıdır](../overview.md#code-style-analysis). Tüm olası önem derecesi değerleri için bkz. [önem düzeyi](../configuration-options.md#severity-level).

## <a name="example"></a>Örnek

Aşağıdaki *. editorconfig* dosyası, ortak özellikler, Yöntemler, alanlar, olaylar ve temsilcilerin büyük harfli olması gerektiğini belirten bir adlandırma kuralı içerir. Bu adlandırma kuralının, bir değeri ayırmak için bir virgül kullanarak kuralın uygulanacağı birden çok sembol türünü belirttiğinden emin olun.

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="see-also"></a>Ayrıca bkz.

- [Dil kuralları](language-rules.md)
- [Biçimlendirme kuralları](formatting-rules.md)
- [Roslyn adlandırma kuralları](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [.NET kod stili kuralları başvurusu](index.md)
