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
ms.openlocfilehash: a61d0ca8684134207a11f79e382b6aaf843ba956
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873256"
---
# <a name="naming-rules"></a><span data-ttu-id="3fbbb-103">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="3fbbb-103">Naming rules</span></span>

<span data-ttu-id="3fbbb-104">`.editorconfig`Dosyanızda sınıflar, Özellikler ve yöntemler gibi .NET programlama dil kodu öğelerinin nasıl adlandırılması gerektiğini belirten ve zorlayabileceğiniz **adlandırma kuralları** tanımlayabilirsiniz &mdash; &mdash; .</span><span class="sxs-lookup"><span data-stu-id="3fbbb-104">In your `.editorconfig` file, you can define **naming rules** that specify and enforce how .NET programming language code elements&mdash;such as classes, properties, and methods&mdash;should be named.</span></span> <span data-ttu-id="3fbbb-105">Örneğin, genel üyelerin büyük harfle veya özel alanların ile başlaması gerektiğini belirtebilirsiniz `_` .</span><span class="sxs-lookup"><span data-stu-id="3fbbb-105">For example, you can specify that public members must be capitalized, or that private fields must begin with `_`.</span></span>

<span data-ttu-id="3fbbb-106">Adlandırma kuralında üç bileşen vardır:</span><span class="sxs-lookup"><span data-stu-id="3fbbb-106">A naming rule has three components:</span></span>

* <span data-ttu-id="3fbbb-107">Kuralın geçerli olduğu **sembol grubu** , örneğin, Genel Üyeler veya özel alanlar.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-107">The **symbol group** that the rule applies to, for example, public members or private fields.</span></span>
* <span data-ttu-id="3fbbb-108">Kuralla ilişkilendirilecek **adlandırma stili** , örneğin, adın büyük harfli olması veya bir alt çizgiyle başlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-108">The **naming style** to associate with the rule, for example, that the name must be capitalized or start with an underscore.</span></span>
* <span data-ttu-id="3fbbb-109">Kuralı zorlamaya yönelik önem derecesi.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-109">The severity for enforcing the convention.</span></span>

<span data-ttu-id="3fbbb-110">İlk olarak, sembol grubunu ve adlandırma stilini belirtmeniz ve bunların her birine bir başlık vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-110">First, you must specify the symbol group and naming style and give each of them a title.</span></span> <span data-ttu-id="3fbbb-111">Ardından, her şeyi birbirine bağlayan adlandırma kuralını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-111">Then you specify the naming rule, which links everything together.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="3fbbb-112">Genel sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fbbb-112">General syntax</span></span>

<span data-ttu-id="3fbbb-113">Adlandırma kuralı, sembol grubu veya adlandırma stili tanımlamak için aşağıdaki sözdizimini kullanarak bir veya daha fazla özellik ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="3fbbb-113">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="3fbbb-114">Her özellik yalnızca bir kez ayarlanmalıdır, ancak bazı ayarlar birden fazla virgülle ayrılmış değere izin verir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-114">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="3fbbb-115">Özelliklerin sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-115">The order of the properties is not important.</span></span>

### \<kind>

<span data-ttu-id="3fbbb-116">**\<kind>** Hangi tür öğe tanımlandığını belirtir &mdash; adlandırma kuralı, sembol grubu veya adlandırma stili &mdash; ve aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3fbbb-116">**\<kind>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="3fbbb-117">Bir özelliği ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3fbbb-117">To set a property for</span></span> | <span data-ttu-id="3fbbb-118">Değeri kullanın \<kind></span><span class="sxs-lookup"><span data-stu-id="3fbbb-118">Use the \<kind> value</span></span> | <span data-ttu-id="3fbbb-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fbbb-119">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="3fbbb-120">Adlandırma kuralı</span><span class="sxs-lookup"><span data-stu-id="3fbbb-120">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="3fbbb-121">Sembol grubu</span><span class="sxs-lookup"><span data-stu-id="3fbbb-121">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="3fbbb-122">Adlandırma stili</span><span class="sxs-lookup"><span data-stu-id="3fbbb-122">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="3fbbb-123">Her tanım &mdash; [adlandırma kuralı](#naming-rule-properties), [sembol grubu](#symbol-group-properties)veya [adlandırma stilinin](#naming-style-properties)her türü, &mdash; Aşağıdaki bölümlerde açıklandığı gibi kendi desteklenen özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-123">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="3fbbb-124">**\<title>** , birden çok özellik ayarını tek bir tanım halinde ilişkilendiğinde seçeceğiniz açıklayıcı bir addır.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-124">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="3fbbb-125">Örneğin, aşağıdaki özellikler iki sembol grubu tanımı üretir `interface` ve `types` her birinin üzerinde iki özelliği ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-125">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="3fbbb-126">Adlandırma kuralı özellikleri</span><span class="sxs-lookup"><span data-stu-id="3fbbb-126">Naming rule properties</span></span>

<span data-ttu-id="3fbbb-127">Kuralın etkili olması için tüm adlandırma kuralı özellikleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-127">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="3fbbb-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="3fbbb-128">Property</span></span> | <span data-ttu-id="3fbbb-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fbbb-129">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="3fbbb-130">Bir sembol grubunun başlığı; adlandırma kuralı bu gruptaki simgelere uygulanacak</span><span class="sxs-lookup"><span data-stu-id="3fbbb-130">The title of a symbol group; the naming rule will be applied to the symbols in this group</span></span> |
| `style` | <span data-ttu-id="3fbbb-131">Bu kuralla ilişkilendirilmesi gereken adlandırma stilinin başlığı</span><span class="sxs-lookup"><span data-stu-id="3fbbb-131">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="3fbbb-132">Adlandırma kuralını zorlayacağı önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-132">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="3fbbb-133">İlişkili değeri kullanılabilir [önem düzeylerinden](../configuration-options.md#severity-level)birine ayarlayın. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3fbbb-133">Set the associated value to one of the available [severity levels](../configuration-options.md#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="3fbbb-134">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="3fbbb-134">**Notes:**</span></span>

1. <span data-ttu-id="3fbbb-135">Bir adlandırma kuralı içindeki önem derecesi yalnızca Visual Studio gibi geliştirme IDEs 'in içinde olur.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-135">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="3fbbb-136">Bu ayar C# veya VB derleyicileri tarafından anlaşılmaz, bu nedenle derleme sırasında dikkate verilmez.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-136">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="3fbbb-137">Derleme üzerinde adlandırma stili kuralları zorlamak için, bunun yerine [kod kuralı önem derecesi yapılandırmasını](#rule-id-ide1006-naming-rule-violation)kullanarak önem derecesi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-137">To enforce naming style rules on build, you should instead set the severity by using [code rule severity configuration](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="3fbbb-138">Daha fazla bilgi için bu [GitHub sorununa](https://github.com/dotnet/roslyn/issues/44201)bakın.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-138">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="3fbbb-139">Sembol grubu özellikleri</span><span class="sxs-lookup"><span data-stu-id="3fbbb-139">Symbol group properties</span></span>

<span data-ttu-id="3fbbb-140">Hangi simgelerin gruba ekleneceğini sınırlamak için sembol grupları için aşağıdaki özellikleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-140">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="3fbbb-141">Tek bir özellik için birden çok değer belirtmek için değerleri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-141">To specify multiple values for a single property, separate the values with a comma.</span></span>

| <span data-ttu-id="3fbbb-142">Özellik</span><span class="sxs-lookup"><span data-stu-id="3fbbb-142">Property</span></span> | <span data-ttu-id="3fbbb-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fbbb-143">Description</span></span> | <span data-ttu-id="3fbbb-144">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="3fbbb-144">Allowed values</span></span> | <span data-ttu-id="3fbbb-145">Gerekli</span><span class="sxs-lookup"><span data-stu-id="3fbbb-145">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="3fbbb-146">Grup <sup>1</sup> ' deki sembol türleri</span><span class="sxs-lookup"><span data-stu-id="3fbbb-146">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="3fbbb-147">`*` (tüm sembolleri belirtmek için bu değeri kullanın)</span><span class="sxs-lookup"><span data-stu-id="3fbbb-147">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="3fbbb-148">Yes</span><span class="sxs-lookup"><span data-stu-id="3fbbb-148">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="3fbbb-149">Gruptaki sembollerin erişilebilirlik düzeyleri</span><span class="sxs-lookup"><span data-stu-id="3fbbb-149">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="3fbbb-150">`*` (tüm erişilebilirlik düzeylerini belirtmek için bu değeri kullanın)</span><span class="sxs-lookup"><span data-stu-id="3fbbb-150">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="3fbbb-151">`internal` veya `friend`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-151">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="3fbbb-152">`protected_internal` veya `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-152">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="3fbbb-153">`local` (bir yöntem içinde tanımlanan semboller için)</span><span class="sxs-lookup"><span data-stu-id="3fbbb-153">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="3fbbb-154">Yes</span><span class="sxs-lookup"><span data-stu-id="3fbbb-154">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="3fbbb-155">Yalnızca _Tüm_ belirtilen değiştiricilere sahip sembolleri Eşleştir <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3fbbb-155">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="3fbbb-156">`abstract` veya `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-156">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="3fbbb-157">`static` veya `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3fbbb-157">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="3fbbb-158">Hayır</span><span class="sxs-lookup"><span data-stu-id="3fbbb-158">No</span></span> |

<span data-ttu-id="3fbbb-159">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="3fbbb-159">**Notes:**</span></span>

1. <span data-ttu-id="3fbbb-160">Demet üyeleri şu anda sürümünde desteklenmemektedir `applicable_kinds` .</span><span class="sxs-lookup"><span data-stu-id="3fbbb-160">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="3fbbb-161">Sembol grubu, özelliğindeki _Tüm_ değiştiricilerin eşleşir `required_modifiers` .</span><span class="sxs-lookup"><span data-stu-id="3fbbb-161">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="3fbbb-162">Bu özelliği atlarsanız, eşleşme için belirli bir değiştirici gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-162">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="3fbbb-163">Bu, sembolün değiştiricilerin bu kuralın uygulanıp uygulanmadığı üzerinde hiçbir etkisi olmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-163">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="3fbbb-164">Grubunuz `static` özelliğinde veya özelliğine sahipse `shared` `required_modifiers` , gruplar örtülü olduklarından, semboller de içerecektir `const` `static` / `Shared` .</span><span class="sxs-lookup"><span data-stu-id="3fbbb-164">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="3fbbb-165">Ancak, `static` adlandırma kuralının semboller için uygulanmasını istemiyorsanız `const` sembol grubu ile yeni bir adlandırma kuralı oluşturabilirsiniz `const` .</span><span class="sxs-lookup"><span data-stu-id="3fbbb-165">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="3fbbb-166">Adlandırma stili özellikleri</span><span class="sxs-lookup"><span data-stu-id="3fbbb-166">Naming style properties</span></span>

<span data-ttu-id="3fbbb-167">Adlandırma stili, kuralla zorlamak istediğiniz kuralları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-167">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="3fbbb-168">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3fbbb-168">For example:</span></span>

* <span data-ttu-id="3fbbb-169">Büyük harfe çevir `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-169">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="3fbbb-170">İle başlar `m_`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-170">Starts with `m_`</span></span>
* <span data-ttu-id="3fbbb-171">Şununla biter `_g`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-171">Ends with `_g`</span></span>
* <span data-ttu-id="3fbbb-172">Sözcükleri ile ayır `__`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-172">Separate words with `__`</span></span>

<span data-ttu-id="3fbbb-173">Adlandırma stili için aşağıdaki özellikleri ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fbbb-173">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="3fbbb-174">Özellik</span><span class="sxs-lookup"><span data-stu-id="3fbbb-174">Property</span></span> | <span data-ttu-id="3fbbb-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fbbb-175">Description</span></span> | <span data-ttu-id="3fbbb-176">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="3fbbb-176">Allowed values</span></span> | <span data-ttu-id="3fbbb-177">Gerekli</span><span class="sxs-lookup"><span data-stu-id="3fbbb-177">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="3fbbb-178">Sembol içindeki sözcüklerin büyük küçük harf stili</span><span class="sxs-lookup"><span data-stu-id="3fbbb-178">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="3fbbb-179">Evet<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3fbbb-179">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="3fbbb-180">Bu karakterlerle başlaması gerekir</span><span class="sxs-lookup"><span data-stu-id="3fbbb-180">Must begin with these characters</span></span> | | <span data-ttu-id="3fbbb-181">Hayır</span><span class="sxs-lookup"><span data-stu-id="3fbbb-181">No</span></span> |
| `required_suffix` | <span data-ttu-id="3fbbb-182">Bu karakterlerle bitmelidir</span><span class="sxs-lookup"><span data-stu-id="3fbbb-182">Must end with these characters</span></span> | | <span data-ttu-id="3fbbb-183">Hayır</span><span class="sxs-lookup"><span data-stu-id="3fbbb-183">No</span></span> |
| `word_separator` | <span data-ttu-id="3fbbb-184">Simgenin içindeki sözcüklerin bu karakterle ayrılması gerekir</span><span class="sxs-lookup"><span data-stu-id="3fbbb-184">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="3fbbb-185">Hayır</span><span class="sxs-lookup"><span data-stu-id="3fbbb-185">No</span></span> |

<span data-ttu-id="3fbbb-186">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="3fbbb-186">**Notes:**</span></span>

1. <span data-ttu-id="3fbbb-187">Adlandırma stiliniz kapsamında bir büyük harf stili belirtmeniz gerekir, aksi takdirde adlandırma stiliniz yok sayılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-187">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="rule-order"></a><span data-ttu-id="3fbbb-188">Kural sırası</span><span class="sxs-lookup"><span data-stu-id="3fbbb-188">Rule order</span></span>

<span data-ttu-id="3fbbb-189">Adlandırma kurallarının bir EditorConfig dosyasında tanımlandığı sıra bu şekilde değildir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-189">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="3fbbb-190">Adlandırma kuralları kuralların tanımına göre otomatik olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-190">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="3fbbb-191">[Editorconfig dil hizmeti uzantısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) , bir editorconfig dosyasını çözümleyebilir ve dosyadaki kural sıralaması derleyicinin çalışma zamanında kullandıklarıyla farklı olduğunda rapor durumlarını rapor edebilir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-191">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="3fbbb-192">Visual Studio 'nun Visual Studio 2019 sürüm 16,2 ' den önceki bir sürümünü kullanıyorsanız, adlandırma kuralları, EditorConfig dosyasında en çok belirli olan en az özel olarak sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-192">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="3fbbb-193">Uygulanabilecek ilk kural, uygulanan tek kuraldır.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-193">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="3fbbb-194">Ancak, aynı ada sahip birden fazla kural *özelliği* varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-194">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="3fbbb-195">Daha fazla bilgi için bkz. [Dosya hiyerarşisi ve önceliği](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span><span class="sxs-lookup"><span data-stu-id="3fbbb-195">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="3fbbb-196">Varsayılan adlandırma stilleri</span><span class="sxs-lookup"><span data-stu-id="3fbbb-196">Default naming styles</span></span>

<span data-ttu-id="3fbbb-197">Herhangi bir özel adlandırma kuralı belirtmezseniz, aşağıdaki varsayılan stiller kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3fbbb-197">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="3fbbb-198">,,, Veya erişilebilirlik ile sınıflar, yapılar, numaralandırmalar, Özellikler ve olaylar için `public` `private` `internal` `protected` `protected_internal` varsayılan adlandırma stili, Pascal durumdur.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-198">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="3fbbb-199">,,, `public` Veya erişilebilirliği olan arabirimler için `private` `internal` `protected` `protected_internal` , varsayılan adlandırma stili, gerekli bir **I** ön eki olan Pascal durumdur.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-199">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="3fbbb-200">Kod kuralı KIMLIĞI: `IDE1006 (Naming rule violation)`</span><span class="sxs-lookup"><span data-stu-id="3fbbb-200">Code Rule ID: `IDE1006 (Naming rule violation)`</span></span>

<span data-ttu-id="3fbbb-201">Tüm adlandırma seçeneklerinin kural KIMLIĞI `IDE1006` ve başlığı vardır `Naming rule violation` .</span><span class="sxs-lookup"><span data-stu-id="3fbbb-201">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="3fbbb-202">Aşağıdaki söz dizimine sahip bir EditorConfig dosyasında genel olarak adlandırma ihlallerinin önem derecesini yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fbbb-202">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="3fbbb-203">Önem derecesi değeri, `warning` `error` [derleme üzerinde zorlanmalıdır](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="3fbbb-203">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="3fbbb-204">Tüm olası önem derecesi değerleri için bkz. [önem düzeyi](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="3fbbb-204">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="example"></a><span data-ttu-id="3fbbb-205">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fbbb-205">Example</span></span>

<span data-ttu-id="3fbbb-206">Aşağıdaki *. editorconfig* dosyası, ortak özellikler, Yöntemler, alanlar, olaylar ve temsilcilerin büyük harfli olması gerektiğini belirten bir adlandırma kuralı içerir.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-206">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="3fbbb-207">Bu adlandırma kuralının, bir değeri ayırmak için bir virgül kullanarak kuralın uygulanacağı birden çok sembol türünü belirttiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-207">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3fbbb-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fbbb-208">See also</span></span>

- [<span data-ttu-id="3fbbb-209">Dil kuralları</span><span class="sxs-lookup"><span data-stu-id="3fbbb-209">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="3fbbb-210">Biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="3fbbb-210">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="3fbbb-211">Roslyn adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="3fbbb-211">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/main/.editorconfig#L63)
- [<span data-ttu-id="3fbbb-212">.NET kod stili kuralları başvurusu</span><span class="sxs-lookup"><span data-stu-id="3fbbb-212">.NET code style rules reference</span></span>](index.md)
