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
ms.openlocfilehash: 8ce209e64ee7f9f9028c221daedef8fc6a993ef7
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96590070"
---
# <a name="naming-rules"></a><span data-ttu-id="a37a3-103">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="a37a3-103">Naming rules</span></span>

<span data-ttu-id="a37a3-104">Adlandırma kuralları, sınıflar, Özellikler ve yöntemler gibi .NET programlama dil kodu öğelerinin adlandırılmasına da yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-104">Naming rules concern the naming of .NET programming language code elements, such as classes, properties, and methods.</span></span> <span data-ttu-id="a37a3-105">Örneğin, genel üyelerin büyük harfle veya özel alanların ile başlaması gerektiğini belirtebilirsiniz `_` .</span><span class="sxs-lookup"><span data-stu-id="a37a3-105">For example, you can specify that public members must be capitalized or that private fields must begin with `_`.</span></span>

<span data-ttu-id="a37a3-106">Adlandırma kuralı üç bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="a37a3-106">A naming rule has three parts:</span></span>

* <span data-ttu-id="a37a3-107">Uygulanan sembol grubu.</span><span class="sxs-lookup"><span data-stu-id="a37a3-107">The group of symbols it applies to.</span></span>
* <span data-ttu-id="a37a3-108">Kuralla ilişkilendirilecek adlandırma stili.</span><span class="sxs-lookup"><span data-stu-id="a37a3-108">The naming style to associate with the rule.</span></span>
* <span data-ttu-id="a37a3-109">Kuralı zorlamaya yönelik önem derecesi.</span><span class="sxs-lookup"><span data-stu-id="a37a3-109">The severity for enforcing the convention.</span></span>

<span data-ttu-id="a37a3-110">Adlandırma kurallarını bir EditorConfig dosyasında tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a37a3-110">You define naming rules in an EditorConfig file.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="a37a3-111">Genel sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a37a3-111">General syntax</span></span>

<span data-ttu-id="a37a3-112">Adlandırma kuralı, sembol grubu veya adlandırma stili tanımlamak için aşağıdaki sözdizimini kullanarak bir veya daha fazla özellik ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="a37a3-112">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<prefix>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="a37a3-113">Her özellik yalnızca bir kez ayarlanmalıdır, ancak bazı ayarlar birden fazla virgülle ayrılmış değere izin verir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-113">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="a37a3-114">Özelliklerin sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-114">The order of the properties is not important.</span></span>

### \<prefix>

<span data-ttu-id="a37a3-115">**\<prefix>** Hangi tür öğe tanımlandığını belirtir &mdash; adlandırma kuralı, sembol grubu veya adlandırma stili &mdash; ve aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a37a3-115">**\<prefix>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="a37a3-116">Bir özelliği ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a37a3-116">To set a property for</span></span> | <span data-ttu-id="a37a3-117">Ön eki kullan</span><span class="sxs-lookup"><span data-stu-id="a37a3-117">Use the prefix</span></span> | <span data-ttu-id="a37a3-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a37a3-118">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="a37a3-119">Adlandırma kuralı</span><span class="sxs-lookup"><span data-stu-id="a37a3-119">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="a37a3-120">Sembol grubu</span><span class="sxs-lookup"><span data-stu-id="a37a3-120">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="a37a3-121">Adlandırma stili</span><span class="sxs-lookup"><span data-stu-id="a37a3-121">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="a37a3-122">Her tanım &mdash; [adlandırma kuralı](#naming-rule-properties), [sembol grubu](#symbol-group-properties)veya [adlandırma stilinin](#naming-style-properties)her türü, &mdash; Aşağıdaki bölümlerde açıklandığı gibi kendi desteklenen özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-122">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="a37a3-123">**\<title>** , birden çok özellik ayarını tek bir tanım halinde ilişkilendiğinde seçeceğiniz açıklayıcı bir addır.</span><span class="sxs-lookup"><span data-stu-id="a37a3-123">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="a37a3-124">Örneğin, aşağıdaki özellikler iki sembol grubu tanımı üretir `interface` ve `types` her birinin üzerinde iki özelliği ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="a37a3-124">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="a37a3-125">Adlandırma kuralı özellikleri</span><span class="sxs-lookup"><span data-stu-id="a37a3-125">Naming rule properties</span></span>

<span data-ttu-id="a37a3-126">Kuralın etkili olması için tüm adlandırma kuralı özellikleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-126">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="a37a3-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="a37a3-127">Property</span></span> | <span data-ttu-id="a37a3-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a37a3-128">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="a37a3-129">Bu kuralın uygulanacağı sembolleri tanımlayarak sembol grubunun başlığı</span><span class="sxs-lookup"><span data-stu-id="a37a3-129">The title of the symbol group, defining the symbols to which this rule should be applied</span></span> |
| `style` | <span data-ttu-id="a37a3-130">Bu kuralla ilişkilendirilmesi gereken adlandırma stilinin başlığı</span><span class="sxs-lookup"><span data-stu-id="a37a3-130">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="a37a3-131">Adlandırma kuralını zorlayacağı önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a37a3-131">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="a37a3-132">İlişkili değeri kullanılabilir [önem düzeylerinden](https://docs.microsoft.com/dotnet/fundamentals/code-analysis/configuration-options#severity-level)birine ayarlayın. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a37a3-132">Set the associated value to one of the available [severity levels](https://docs.microsoft.com/dotnet/fundamentals/code-analysis/configuration-options#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="a37a3-133">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="a37a3-133">**Notes:**</span></span>

1. <span data-ttu-id="a37a3-134">Bir adlandırma kuralı içindeki önem derecesi yalnızca Visual Studio gibi geliştirme IDEs 'in içinde olur.</span><span class="sxs-lookup"><span data-stu-id="a37a3-134">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="a37a3-135">Bu ayar C# veya VB derleyicileri tarafından anlaşılmaz, bu nedenle derleme sırasında dikkate verilmez.</span><span class="sxs-lookup"><span data-stu-id="a37a3-135">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="a37a3-136">Bunun yerine, derlemede adlandırma stil kurallarını zorlamak için, [Bu bölümde](#rule-id-ide1006-naming-rule-violation)açıklandığı gıbı kural kimliği tabanlı önem derecesi yapılandırmasını kullanarak önem derecesini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-136">Instead, to enforce naming style rules on build, you should set the severity by using the rule ID-based severity configuration as explained in [this section](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="a37a3-137">Daha fazla bilgi için bu [GitHub sorununa](https://github.com/dotnet/roslyn/issues/44201)bakın.</span><span class="sxs-lookup"><span data-stu-id="a37a3-137">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="rule-order"></a><span data-ttu-id="a37a3-138">Kural sırası</span><span class="sxs-lookup"><span data-stu-id="a37a3-138">Rule order</span></span>

<span data-ttu-id="a37a3-139">Adlandırma kurallarının bir EditorConfig dosyasında tanımlandığı sıra bu şekilde değildir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-139">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="a37a3-140">Adlandırma kuralları kuralların tanımına göre otomatik olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="a37a3-140">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="a37a3-141">[Editorconfig dil hizmeti uzantısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) , bir editorconfig dosyasını çözümleyebilir ve dosyadaki kural sıralaması derleyicinin çalışma zamanında kullandıklarıyla farklı olduğunda rapor durumlarını rapor edebilir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-141">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="a37a3-142">Visual Studio 'nun Visual Studio 2019 sürüm 16,2 ' den önceki bir sürümünü kullanıyorsanız, adlandırma kuralları, EditorConfig dosyasında en çok belirli olan en az özel olarak sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a37a3-142">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="a37a3-143">Uygulanabilecek ilk kural, uygulanan tek kuraldır.</span><span class="sxs-lookup"><span data-stu-id="a37a3-143">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="a37a3-144">Ancak, aynı ada sahip birden fazla kural *özelliği* varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="a37a3-144">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="a37a3-145">Daha fazla bilgi için bkz. [Dosya hiyerarşisi ve önceliği](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span><span class="sxs-lookup"><span data-stu-id="a37a3-145">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="a37a3-146">Sembol grubu özellikleri</span><span class="sxs-lookup"><span data-stu-id="a37a3-146">Symbol group properties</span></span>

<span data-ttu-id="a37a3-147">Hangi simgelerin gruba ekleneceğini sınırlamak için sembol grupları için aşağıdaki özellikleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a37a3-147">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="a37a3-148">Tek bir özellik ayarında birden çok değer belirtmek için bunları virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="a37a3-148">To specify multiple values in a single property setting, separate them with a comma.</span></span>

| <span data-ttu-id="a37a3-149">Özellik</span><span class="sxs-lookup"><span data-stu-id="a37a3-149">Property</span></span> | <span data-ttu-id="a37a3-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a37a3-150">Description</span></span> | <span data-ttu-id="a37a3-151">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="a37a3-151">Allowed values</span></span> | <span data-ttu-id="a37a3-152">Gerekli</span><span class="sxs-lookup"><span data-stu-id="a37a3-152">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="a37a3-153">Grup <sup>1</sup> ' deki sembol türleri</span><span class="sxs-lookup"><span data-stu-id="a37a3-153">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="a37a3-154">`*` (tüm sembolleri belirtmek için bu değeri kullanın)</span><span class="sxs-lookup"><span data-stu-id="a37a3-154">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="a37a3-155">Evet</span><span class="sxs-lookup"><span data-stu-id="a37a3-155">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="a37a3-156">Gruptaki sembollerin erişilebilirlik düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a37a3-156">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="a37a3-157">`*` (tüm erişilebilirlik düzeylerini belirtmek için bu değeri kullanın)</span><span class="sxs-lookup"><span data-stu-id="a37a3-157">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="a37a3-158">`internal` veya `friend`</span><span class="sxs-lookup"><span data-stu-id="a37a3-158">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="a37a3-159">`protected_internal` veya `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="a37a3-159">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="a37a3-160">`local` (bir yöntem içinde tanımlanan semboller için)</span><span class="sxs-lookup"><span data-stu-id="a37a3-160">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="a37a3-161">Evet</span><span class="sxs-lookup"><span data-stu-id="a37a3-161">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="a37a3-162">Yalnızca _Tüm_ belirtilen değiştiricilere sahip sembolleri Eşleştir <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="a37a3-162">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="a37a3-163">`abstract` veya `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="a37a3-163">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="a37a3-164">`static` veya `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="a37a3-164">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="a37a3-165">Hayır</span><span class="sxs-lookup"><span data-stu-id="a37a3-165">No</span></span> |

<span data-ttu-id="a37a3-166">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="a37a3-166">**Notes:**</span></span>

1. <span data-ttu-id="a37a3-167">Demet üyeleri şu anda sürümünde desteklenmemektedir `applicable_kinds` .</span><span class="sxs-lookup"><span data-stu-id="a37a3-167">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="a37a3-168">Sembol grubu, özelliğindeki _Tüm_ değiştiricilerin eşleşir `required_modifiers` .</span><span class="sxs-lookup"><span data-stu-id="a37a3-168">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="a37a3-169">Bu özelliği atlarsanız, eşleşme için belirli bir değiştirici gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a37a3-169">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="a37a3-170">Bu, sembolün değiştiricilerin bu kuralın uygulanıp uygulanmadığı üzerinde hiçbir etkisi olmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-170">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="a37a3-171">Grubunuz `static` özelliğinde veya özelliğine sahipse `shared` `required_modifiers` , gruplar örtülü olduklarından, semboller de içerecektir `const` `static` / `Shared` .</span><span class="sxs-lookup"><span data-stu-id="a37a3-171">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="a37a3-172">Ancak, `static` adlandırma kuralının semboller için uygulanmasını istemiyorsanız `const` sembol grubu ile yeni bir adlandırma kuralı oluşturabilirsiniz `const` .</span><span class="sxs-lookup"><span data-stu-id="a37a3-172">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="a37a3-173">Adlandırma stili özellikleri</span><span class="sxs-lookup"><span data-stu-id="a37a3-173">Naming style properties</span></span>

<span data-ttu-id="a37a3-174">Adlandırma stili, kuralla zorlamak istediğiniz kuralları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a37a3-174">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="a37a3-175">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a37a3-175">For example:</span></span>

* <span data-ttu-id="a37a3-176">Büyük harfe çevir `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="a37a3-176">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="a37a3-177">İle başlar `m_`</span><span class="sxs-lookup"><span data-stu-id="a37a3-177">Starts with `m_`</span></span>
* <span data-ttu-id="a37a3-178">Şununla biter `_g`</span><span class="sxs-lookup"><span data-stu-id="a37a3-178">Ends with `_g`</span></span>
* <span data-ttu-id="a37a3-179">Sözcükleri ile ayır `__`</span><span class="sxs-lookup"><span data-stu-id="a37a3-179">Separate words with `__`</span></span>

<span data-ttu-id="a37a3-180">Adlandırma stili için aşağıdaki özellikleri ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a37a3-180">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="a37a3-181">Özellik</span><span class="sxs-lookup"><span data-stu-id="a37a3-181">Property</span></span> | <span data-ttu-id="a37a3-182">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a37a3-182">Description</span></span> | <span data-ttu-id="a37a3-183">İzin verilen değerler</span><span class="sxs-lookup"><span data-stu-id="a37a3-183">Allowed values</span></span> | <span data-ttu-id="a37a3-184">Gerekli</span><span class="sxs-lookup"><span data-stu-id="a37a3-184">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="a37a3-185">Sembol içindeki sözcüklerin büyük küçük harf stili</span><span class="sxs-lookup"><span data-stu-id="a37a3-185">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="a37a3-186">Evet<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a37a3-186">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="a37a3-187">Bu karakterlerle başlaması gerekir</span><span class="sxs-lookup"><span data-stu-id="a37a3-187">Must begin with these characters</span></span> | | <span data-ttu-id="a37a3-188">Hayır</span><span class="sxs-lookup"><span data-stu-id="a37a3-188">No</span></span> |
| `required_suffix` | <span data-ttu-id="a37a3-189">Bu karakterlerle bitmelidir</span><span class="sxs-lookup"><span data-stu-id="a37a3-189">Must end with these characters</span></span> | | <span data-ttu-id="a37a3-190">Hayır</span><span class="sxs-lookup"><span data-stu-id="a37a3-190">No</span></span> |
| `word_separator` | <span data-ttu-id="a37a3-191">Simgenin içindeki sözcüklerin bu karakterle ayrılması gerekir</span><span class="sxs-lookup"><span data-stu-id="a37a3-191">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="a37a3-192">Hayır</span><span class="sxs-lookup"><span data-stu-id="a37a3-192">No</span></span> |

<span data-ttu-id="a37a3-193">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="a37a3-193">**Notes:**</span></span>

1. <span data-ttu-id="a37a3-194">Adlandırma stiliniz kapsamında bir büyük harf stili belirtmeniz gerekir, aksi takdirde adlandırma stiliniz yok sayılabilir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-194">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="a37a3-195">Varsayılan adlandırma stilleri</span><span class="sxs-lookup"><span data-stu-id="a37a3-195">Default naming styles</span></span>

<span data-ttu-id="a37a3-196">Herhangi bir özel adlandırma kuralı belirtmezseniz, aşağıdaki varsayılan stiller kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a37a3-196">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="a37a3-197">,,, Veya erişilebilirlik ile sınıflar, yapılar, numaralandırmalar, Özellikler ve olaylar için `public` `private` `internal` `protected` `protected_internal` varsayılan adlandırma stili, Pascal durumdur.</span><span class="sxs-lookup"><span data-stu-id="a37a3-197">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="a37a3-198">,,, `public` Veya erişilebilirliği olan arabirimler için `private` `internal` `protected` `protected_internal` , varsayılan adlandırma stili, gerekli bir **I** ön eki olan Pascal durumdur.</span><span class="sxs-lookup"><span data-stu-id="a37a3-198">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="example"></a><span data-ttu-id="a37a3-199">Örnek</span><span class="sxs-lookup"><span data-stu-id="a37a3-199">Example</span></span>

<span data-ttu-id="a37a3-200">Aşağıdaki *. editorconfig* dosyası, ortak özellikler, Yöntemler, alanlar, olaylar ve temsilcilerin büyük harfli olması gerektiğini belirten bir adlandırma kuralı içerir.</span><span class="sxs-lookup"><span data-stu-id="a37a3-200">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="a37a3-201">Bu adlandırma kuralının, bir değeri ayırmak için bir virgül kullanarak kuralın uygulanacağı birden çok sembol türünü belirttiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a37a3-201">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="a37a3-202">Kural KIMLIĞI: "IDE1006" (adlandırma kuralı ihlali)</span><span class="sxs-lookup"><span data-stu-id="a37a3-202">Rule ID: "IDE1006" (Naming rule violation)</span></span>

<span data-ttu-id="a37a3-203">Tüm adlandırma seçeneklerinin kural KIMLIĞI `IDE1006` ve başlığı vardır `Naming rule violation` .</span><span class="sxs-lookup"><span data-stu-id="a37a3-203">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="a37a3-204">Aşağıdaki söz dizimine sahip bir EditorConfig dosyasında genel olarak adlandırma ihlallerinin önem derecesini yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a37a3-204">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="a37a3-205">Önem derecesi değeri, `warning` `error` [derleme üzerinde zorlanmalıdır](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="a37a3-205">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="a37a3-206">Tüm olası önem derecesi değerleri için bkz. [önem düzeyi](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="a37a3-206">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="see-also"></a><span data-ttu-id="a37a3-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a37a3-207">See also</span></span>

- [<span data-ttu-id="a37a3-208">Dil kuralları</span><span class="sxs-lookup"><span data-stu-id="a37a3-208">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="a37a3-209">Biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="a37a3-209">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="a37a3-210">Roslyn adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="a37a3-210">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [<span data-ttu-id="a37a3-211">.NET kod stili kuralları başvurusu</span><span class="sxs-lookup"><span data-stu-id="a37a3-211">.NET code style rules reference</span></span>](index.md)
