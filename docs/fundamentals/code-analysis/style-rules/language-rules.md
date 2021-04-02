---
title: Kod stili dil kuralları
description: C# ve Visual Basic dil yapılarını kullanmaya yönelik farklı kod stili kuralları hakkında bilgi edinin.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
- language rules
- EditorConfig language conventions
ms.openlocfilehash: 2aa2261534363f1da6a2109f092e08d210ebd915
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "98957981"
---
# <a name="language-rules"></a><span data-ttu-id="4cd5f-103">Dil kuralları</span><span class="sxs-lookup"><span data-stu-id="4cd5f-103">Language rules</span></span>

<span data-ttu-id="4cd5f-104">Kod stili dil kuralları, .NET programlama dillerinin çeşitli yapılarının, örneğin değiştiricilerin ve parantezlerin nasıl kullanıldığını etkiler.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-104">Code style language rules affect how various constructs of .NET programming languages, for example, modifiers and parentheses, are used.</span></span> <span data-ttu-id="4cd5f-105">Kurallar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="4cd5f-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="4cd5f-106">[.Net stil kuralları](#net-style-rules): hem C# hem de Visual Basic için uygulanan kurallar.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-106">[.NET style rules](#net-style-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="4cd5f-107">Bu kuralların EditorConfig seçenek adları `dotnet_style_` ön Ekle başlar.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-107">The EditorConfig option names for these rules start with `dotnet_style_` prefix.</span></span>
- <span data-ttu-id="4cd5f-108">[C# stil kuralları](#c-style-rules): yalnızca c# diline özgü kurallardır.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-108">[C# style rules](#c-style-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="4cd5f-109">Bu kuralların EditorConfig seçenek adları `csharp_style_` ön Ekle başlar.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-109">The EditorConfig option names for these rules start with `csharp_style_` prefix.</span></span>
- <span data-ttu-id="4cd5f-110">[Visual Basic stil kuralları](#visual-basic-style-rules): yalnızca Visual Bsic diline özgü kurallardır.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-110">[Visual Basic style rules](#visual-basic-style-rules): Rules that are specific to Visual Bsic language only.</span></span> <span data-ttu-id="4cd5f-111">Bu kuralların EditorConfig seçenek adları `visual_basic_style_` ön Ekle başlar.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-111">The EditorConfig option names for these rules start with `visual_basic_style_` prefix.</span></span>

## <a name="option-format"></a><span data-ttu-id="4cd5f-112">Seçenek biçimi</span><span class="sxs-lookup"><span data-stu-id="4cd5f-112">Option format</span></span>

<span data-ttu-id="4cd5f-113">Dil kuralları seçenekleri aşağıdaki biçimde bir EditorConfig dosyasında belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="4cd5f-113">Options for language rules can be specified in an EditorConfig file with the following format:</span></span>

<span data-ttu-id="4cd5f-114">`option_name = value` (Visual Studio 2019 sürüm 16,9 Preview 2 ve üzeri)</span><span class="sxs-lookup"><span data-stu-id="4cd5f-114">`option_name = value` (Visual Studio 2019 version 16.9 Preview 2 and later)</span></span>

<span data-ttu-id="4cd5f-115">veya</span><span class="sxs-lookup"><span data-stu-id="4cd5f-115">or</span></span>

`option_name = value:severity`

- <span data-ttu-id="4cd5f-116">**Değer**</span><span class="sxs-lookup"><span data-stu-id="4cd5f-116">**Value**</span></span>

  <span data-ttu-id="4cd5f-117">Her dil kuralı için, stilin ne zaman tercih edilmesi gerektiğini tanımlayan bir değer belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-117">For each language rule, you specify a value that defines if or when to prefer the style.</span></span> <span data-ttu-id="4cd5f-118">Birçok kural bir değeri kabul eder `true` (Bu stili tercih et) veya `false` (Bu stili tercih etme).</span><span class="sxs-lookup"><span data-stu-id="4cd5f-118">Many rules accept a value of `true` (prefer this style) or `false` (do not prefer this style).</span></span> <span data-ttu-id="4cd5f-119">Diğer kurallar veya gibi değerleri kabul `when_on_single_line` eder `never` .</span><span class="sxs-lookup"><span data-stu-id="4cd5f-119">Other rules accept values such as `when_on_single_line` or `never`.</span></span>

- <span data-ttu-id="4cd5f-120">**Önem derecesi** (Visual Studio 2019 sürüm 16,9 Preview 2 ve sonraki sürümler için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="4cd5f-120">**Severity** (optional in Visual Studio 2019 version 16.9 Preview 2 and later versions)</span></span>

  <span data-ttu-id="4cd5f-121">Kuralın ikinci bölümü, kuralın [önem derecesini](../configuration-options.md#severity-level) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-121">The second part of the rule specifies the [severity level](../configuration-options.md#severity-level) for the rule.</span></span> <span data-ttu-id="4cd5f-122">Bu şekilde belirtildiğinde önem derecesi ayarı yalnızca Visual Studio gibi geliştirme IDEs 'in içinde olur.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-122">When specified in this way, the severity setting is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="4cd5f-123">Derleme sırasında dikkate *verilmez* .</span><span class="sxs-lookup"><span data-stu-id="4cd5f-123">It is *not* respected during build.</span></span>

  <span data-ttu-id="4cd5f-124">Derleme zamanında kod stili kuralları zorlamak için, bunun yerine çözümleyiciler için kural KIMLIĞI tabanlı önem derecesi yapılandırma sözdizimini kullanarak önem derecesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-124">To enforce code style rules at build time, set the severity by using the rule ID-based severity configuration syntax for analyzers instead.</span></span> <span data-ttu-id="4cd5f-125">Sözdizimi, `dotnet_diagnostic.<rule ID>.severity = <severity>` Örneğin, biçimini alır `dotnet_diagnostic.IDE0040.severity = silent` .</span><span class="sxs-lookup"><span data-stu-id="4cd5f-125">The syntax takes the form `dotnet_diagnostic.<rule ID>.severity = <severity>`, for example, `dotnet_diagnostic.IDE0040.severity = silent`.</span></span> <span data-ttu-id="4cd5f-126">Daha fazla bilgi için bkz. [önem düzeyi](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="4cd5f-126">For more information, see [severity level](../configuration-options.md#severity-level).</span></span>

> [!TIP]
>
> <span data-ttu-id="4cd5f-127">Visual Studio 2019 sürüm 16,3 ' den başlayarak, bir stil ihlali oluştuktan sonra [hızlı eylemler](/visualstudio/ide/quick-actions) ampul menüsünden kod stili kurallarını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-127">Starting in Visual Studio 2019 version 16.3, you can configure code style rules from the [Quick Actions](/visualstudio/ide/quick-actions) light bulb menu after a style violation occurs.</span></span> <span data-ttu-id="4cd5f-128">Daha fazla bilgi için bkz. [Visual Studio 'da kod stillerini otomatik olarak yapılandırma](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4cd5f-128">For more information, see [Automatically configure code styles in Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span></span>

## <a name="net-style-rules"></a><span data-ttu-id="4cd5f-129">.NET stil kuralları</span><span class="sxs-lookup"><span data-stu-id="4cd5f-129">.NET style rules</span></span>

<span data-ttu-id="4cd5f-130">Bu bölümdeki stil kuralları hem C# hem de Visual Basic için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-130">The style rules in this section are applicable to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="4cd5f-131">' this. ' ve ' me. ' niteleyicileri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-131">'this.' and 'Me.' qualifiers</span></span>](ide0003-ide0009.md)
  - [<span data-ttu-id="4cd5f-132">dotnet_style_qualification_for_field</span><span class="sxs-lookup"><span data-stu-id="4cd5f-132">dotnet_style_qualification_for_field</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [<span data-ttu-id="4cd5f-133">dotnet_style_qualification_for_property</span><span class="sxs-lookup"><span data-stu-id="4cd5f-133">dotnet_style_qualification_for_property</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [<span data-ttu-id="4cd5f-134">dotnet_style_qualification_for_method</span><span class="sxs-lookup"><span data-stu-id="4cd5f-134">dotnet_style_qualification_for_method</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [<span data-ttu-id="4cd5f-135">dotnet_style_qualification_for_event</span><span class="sxs-lookup"><span data-stu-id="4cd5f-135">dotnet_style_qualification_for_event</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [<span data-ttu-id="4cd5f-136">Tür başvuruları için çerçeve türü adları yerine dil anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-136">Language keywords instead of framework type names for type references</span></span>](ide0049.md)
  - [<span data-ttu-id="4cd5f-137">dotnet_style_predefined_type_for_locals_parameters_members</span><span class="sxs-lookup"><span data-stu-id="4cd5f-137">dotnet_style_predefined_type_for_locals_parameters_members</span></span>](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [<span data-ttu-id="4cd5f-138">dotnet_style_predefined_type_for_member_access</span><span class="sxs-lookup"><span data-stu-id="4cd5f-138">dotnet_style_predefined_type_for_member_access</span></span>](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [<span data-ttu-id="4cd5f-139">Değiştirici tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-139">Modifier preferences</span></span>](modifier-preferences.md#net-modifier-preferences)
  - [<span data-ttu-id="4cd5f-140">dotnet_style_require_accessibility_modifiers</span><span class="sxs-lookup"><span data-stu-id="4cd5f-140">dotnet_style_require_accessibility_modifiers</span></span>](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [<span data-ttu-id="4cd5f-141">csharp_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="4cd5f-141">csharp_preferred_modifier_order</span></span>](ide0036.md#csharp_preferred_modifier_order)
  - [<span data-ttu-id="4cd5f-142">visual_basic_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="4cd5f-142">visual_basic_preferred_modifier_order</span></span>](ide0036.md#visual_basic_preferred_modifier_order)
  - [<span data-ttu-id="4cd5f-143">dotnet_style_readonly_field</span><span class="sxs-lookup"><span data-stu-id="4cd5f-143">dotnet_style_readonly_field</span></span>](ide0044.md#dotnet_style_readonly_field)
- [<span data-ttu-id="4cd5f-144">Parantez tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-144">Parentheses preferences</span></span>](ide0047-ide0048.md)
  - [<span data-ttu-id="4cd5f-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span><span class="sxs-lookup"><span data-stu-id="4cd5f-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [<span data-ttu-id="4cd5f-146">dotnet_style_parentheses_in_relational_binary_operators</span><span class="sxs-lookup"><span data-stu-id="4cd5f-146">dotnet_style_parentheses_in_relational_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [<span data-ttu-id="4cd5f-147">dotnet_style_parentheses_in_other_binary_operators</span><span class="sxs-lookup"><span data-stu-id="4cd5f-147">dotnet_style_parentheses_in_other_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [<span data-ttu-id="4cd5f-148">dotnet_style_parentheses_in_other_operators</span><span class="sxs-lookup"><span data-stu-id="4cd5f-148">dotnet_style_parentheses_in_other_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [<span data-ttu-id="4cd5f-149">İfade düzeyinde tercihler</span><span class="sxs-lookup"><span data-stu-id="4cd5f-149">Expression-level preferences</span></span>](expression-level-preferences.md#net-expression-level-preferences)
  - [<span data-ttu-id="4cd5f-150">dotnet_style_object_initializer</span><span class="sxs-lookup"><span data-stu-id="4cd5f-150">dotnet_style_object_initializer</span></span>](ide0017.md#dotnet_style_object_initializer)
  - [<span data-ttu-id="4cd5f-151">dotnet_style_collection_initializer</span><span class="sxs-lookup"><span data-stu-id="4cd5f-151">dotnet_style_collection_initializer</span></span>](ide0028.md#dotnet_style_collection_initializer)
  - [<span data-ttu-id="4cd5f-152">dotnet_style_explicit_tuple_names</span><span class="sxs-lookup"><span data-stu-id="4cd5f-152">dotnet_style_explicit_tuple_names</span></span>](ide0033.md#dotnet_style_explicit_tuple_names)
  - [<span data-ttu-id="4cd5f-153">dotnet_style_prefer_inferred_tuple_names</span><span class="sxs-lookup"><span data-stu-id="4cd5f-153">dotnet_style_prefer_inferred_tuple_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [<span data-ttu-id="4cd5f-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span><span class="sxs-lookup"><span data-stu-id="4cd5f-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [<span data-ttu-id="4cd5f-155">dotnet_style_prefer_auto_properties</span><span class="sxs-lookup"><span data-stu-id="4cd5f-155">dotnet_style_prefer_auto_properties</span></span>](ide0032.md#dotnet_style_prefer_auto_properties)
  - [<span data-ttu-id="4cd5f-156">dotnet_style_prefer_conditional_expression_over_assignment</span><span class="sxs-lookup"><span data-stu-id="4cd5f-156">dotnet_style_prefer_conditional_expression_over_assignment</span></span>](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [<span data-ttu-id="4cd5f-157">dotnet_style_prefer_conditional_expression_over_return</span><span class="sxs-lookup"><span data-stu-id="4cd5f-157">dotnet_style_prefer_conditional_expression_over_return</span></span>](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [<span data-ttu-id="4cd5f-158">dotnet_style_prefer_compound_assignment</span><span class="sxs-lookup"><span data-stu-id="4cd5f-158">dotnet_style_prefer_compound_assignment</span></span>](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [<span data-ttu-id="4cd5f-159">dotnet_style_prefer_simplified_interpolation</span><span class="sxs-lookup"><span data-stu-id="4cd5f-159">dotnet_style_prefer_simplified_interpolation</span></span>](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [<span data-ttu-id="4cd5f-160">dotnet_style_prefer_simplified_boolean_expressions</span><span class="sxs-lookup"><span data-stu-id="4cd5f-160">dotnet_style_prefer_simplified_boolean_expressions</span></span>](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - <span data-ttu-id="4cd5f-161">[Switch ifadesine eksik durumları Ekle](ide0010.md) -bu kuralda kod stili seçeneği yok.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-161">[Add missing cases to switch statement](ide0010.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="4cd5f-162">[Anonim türü kayıt tipine Dönüştür](ide0050.md) -bu kuralda kod stili seçeneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-162">[Convert anonymous type to tuple](ide0050.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="4cd5f-163">[' System. HashCode. Birleştir ' kullanın](ide0070.md) -bu kuralda kod stili seçeneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-163">[Use 'System.HashCode.Combine'](ide0070.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="4cd5f-164">[' Typeof ' öğesini ' NameOf ' öğesine Dönüştür](ide0082.md) -bu kuralda kod stili seçeneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-164">[Convert 'typeof' to 'nameof'](ide0082.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="4cd5f-165">Null denetleme tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-165">Null-checking preferences</span></span>](null-checking-preferences.md#net-null-checking-preferences)
  - [<span data-ttu-id="4cd5f-166">dotnet_style_coalesce_expression</span><span class="sxs-lookup"><span data-stu-id="4cd5f-166">dotnet_style_coalesce_expression</span></span>](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [<span data-ttu-id="4cd5f-167">dotnet_style_null_propagation</span><span class="sxs-lookup"><span data-stu-id="4cd5f-167">dotnet_style_null_propagation</span></span>](ide0031.md#dotnet_style_null_propagation)
  - [<span data-ttu-id="4cd5f-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span><span class="sxs-lookup"><span data-stu-id="4cd5f-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span></span>](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [<span data-ttu-id="4cd5f-169">Dosya üst bilgisi tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-169">File header preferences</span></span>](ide0073.md)
  - [<span data-ttu-id="4cd5f-170">file_header_template</span><span class="sxs-lookup"><span data-stu-id="4cd5f-170">file_header_template</span></span>](ide0073.md#file_header_template)

## <a name="c-style-rules"></a><span data-ttu-id="4cd5f-171">C# stil kuralları</span><span class="sxs-lookup"><span data-stu-id="4cd5f-171">C# style rules</span></span>

<span data-ttu-id="4cd5f-172">Bu bölümdeki stil kuralları yalnızca C# dili için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-172">The style rules in this section are applicable to C# language only.</span></span>

- [<span data-ttu-id="4cd5f-173">' var ' tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-173">'var' preferences</span></span>](ide0007-ide0008.md)
  - [<span data-ttu-id="4cd5f-174">csharp_style_var_for_built_in_types</span><span class="sxs-lookup"><span data-stu-id="4cd5f-174">csharp_style_var_for_built_in_types</span></span>](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [<span data-ttu-id="4cd5f-175">csharp_style_var_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="4cd5f-175">csharp_style_var_when_type_is_apparent</span></span>](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [<span data-ttu-id="4cd5f-176">csharp_style_var_elsewhere</span><span class="sxs-lookup"><span data-stu-id="4cd5f-176">csharp_style_var_elsewhere</span></span>](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [<span data-ttu-id="4cd5f-177">İfade gövdeli üyeler</span><span class="sxs-lookup"><span data-stu-id="4cd5f-177">Expression-bodied members</span></span>](expression-bodied-members.md)
  - [<span data-ttu-id="4cd5f-178">csharp_style_expression_bodied_methods</span><span class="sxs-lookup"><span data-stu-id="4cd5f-178">csharp_style_expression_bodied_methods</span></span>](ide0022.md#csharp_style_expression_bodied_methods)
  - [<span data-ttu-id="4cd5f-179">csharp_style_expression_bodied_constructors</span><span class="sxs-lookup"><span data-stu-id="4cd5f-179">csharp_style_expression_bodied_constructors</span></span>](ide0021.md#csharp_style_expression_bodied_constructors)
  - [<span data-ttu-id="4cd5f-180">csharp_style_expression_bodied_operators</span><span class="sxs-lookup"><span data-stu-id="4cd5f-180">csharp_style_expression_bodied_operators</span></span>](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [<span data-ttu-id="4cd5f-181">csharp_style_expression_bodied_properties</span><span class="sxs-lookup"><span data-stu-id="4cd5f-181">csharp_style_expression_bodied_properties</span></span>](ide0025.md#csharp_style_expression_bodied_properties)
  - [<span data-ttu-id="4cd5f-182">csharp_style_expression_bodied_indexers</span><span class="sxs-lookup"><span data-stu-id="4cd5f-182">csharp_style_expression_bodied_indexers</span></span>](ide0026.md#csharp_style_expression_bodied_indexers)
  - [<span data-ttu-id="4cd5f-183">csharp_style_expression_bodied_accessors</span><span class="sxs-lookup"><span data-stu-id="4cd5f-183">csharp_style_expression_bodied_accessors</span></span>](ide0027.md#csharp_style_expression_bodied_accessors)
  - [<span data-ttu-id="4cd5f-184">csharp_style_expression_bodied_lambdas</span><span class="sxs-lookup"><span data-stu-id="4cd5f-184">csharp_style_expression_bodied_lambdas</span></span>](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [<span data-ttu-id="4cd5f-185">csharp_style_expression_bodied_local_functions</span><span class="sxs-lookup"><span data-stu-id="4cd5f-185">csharp_style_expression_bodied_local_functions</span></span>](ide0061.md#csharp_style_expression_bodied_local_functions)
- [<span data-ttu-id="4cd5f-186">Desen eşleştirme tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-186">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="4cd5f-187">csharp_style_pattern_matching_over_is_with_cast_check</span><span class="sxs-lookup"><span data-stu-id="4cd5f-187">csharp_style_pattern_matching_over_is_with_cast_check</span></span>](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [<span data-ttu-id="4cd5f-188">csharp_style_pattern_matching_over_as_with_null_check</span><span class="sxs-lookup"><span data-stu-id="4cd5f-188">csharp_style_pattern_matching_over_as_with_null_check</span></span>](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [<span data-ttu-id="4cd5f-189">csharp_style_prefer_switch_expression</span><span class="sxs-lookup"><span data-stu-id="4cd5f-189">csharp_style_prefer_switch_expression</span></span>](ide0066.md#csharp_style_prefer_switch_expression)
  - [<span data-ttu-id="4cd5f-190">csharp_style_prefer_pattern_matching</span><span class="sxs-lookup"><span data-stu-id="4cd5f-190">csharp_style_prefer_pattern_matching</span></span>](ide0078.md#csharp_style_prefer_pattern_matching)
  - [<span data-ttu-id="4cd5f-191">csharp_style_prefer_not_pattern</span><span class="sxs-lookup"><span data-stu-id="4cd5f-191">csharp_style_prefer_not_pattern</span></span>](ide0083.md#csharp_style_prefer_not_pattern)
- [<span data-ttu-id="4cd5f-192">İfade düzeyinde tercihler</span><span class="sxs-lookup"><span data-stu-id="4cd5f-192">Expression-level preferences</span></span>](expression-level-preferences.md#c-expression-level-preferences)
  - [<span data-ttu-id="4cd5f-193">csharp_style_inlined_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="4cd5f-193">csharp_style_inlined_variable_declaration</span></span>](ide0018.md#csharp_style_inlined_variable_declaration)
  - [<span data-ttu-id="4cd5f-194">csharp_prefer_simple_default_expression</span><span class="sxs-lookup"><span data-stu-id="4cd5f-194">csharp_prefer_simple_default_expression</span></span>](ide0034.md#csharp_prefer_simple_default_expression)
  - [<span data-ttu-id="4cd5f-195">csharp_style_pattern_local_over_anonymous_function</span><span class="sxs-lookup"><span data-stu-id="4cd5f-195">csharp_style_pattern_local_over_anonymous_function</span></span>](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [<span data-ttu-id="4cd5f-196">csharp_style_deconstructed_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="4cd5f-196">csharp_style_deconstructed_variable_declaration</span></span>](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [<span data-ttu-id="4cd5f-197">csharp_style_prefer_index_operator</span><span class="sxs-lookup"><span data-stu-id="4cd5f-197">csharp_style_prefer_index_operator</span></span>](ide0056.md#csharp_style_prefer_index_operator)
  - [<span data-ttu-id="4cd5f-198">csharp_style_prefer_range_operator</span><span class="sxs-lookup"><span data-stu-id="4cd5f-198">csharp_style_prefer_range_operator</span></span>](ide0057.md#csharp_style_prefer_range_operator)
  - [<span data-ttu-id="4cd5f-199">csharp_style_implicit_object_creation_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="4cd5f-199">csharp_style_implicit_object_creation_when_type_is_apparent</span></span>](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - <span data-ttu-id="4cd5f-200">[Anahtar ifadesine eksik durum ekleme](ide0072.md) -bu kuralda kod stili seçeneği yok.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-200">[Add missing cases to switch expression](ide0072.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="4cd5f-201">"Null" Denetim tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-201">"Null" checking preferences</span></span>](null-checking-preferences.md#c-null-checking-preferences)
  - [<span data-ttu-id="4cd5f-202">csharp_style_throw_expression</span><span class="sxs-lookup"><span data-stu-id="4cd5f-202">csharp_style_throw_expression</span></span>](ide0016.md#csharp_style_throw_expression)
  - [<span data-ttu-id="4cd5f-203">csharp_style_conditional_delegate_call</span><span class="sxs-lookup"><span data-stu-id="4cd5f-203">csharp_style_conditional_delegate_call</span></span>](ide1005.md#csharp_style_conditional_delegate_call)
- [<span data-ttu-id="4cd5f-204">Kod bloğu tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-204">Code block preferences</span></span>](code-block-preferences.md)
  - [<span data-ttu-id="4cd5f-205">csharp_prefer_braces</span><span class="sxs-lookup"><span data-stu-id="4cd5f-205">csharp_prefer_braces</span></span>](ide0011.md#csharp_prefer_braces)
  - [<span data-ttu-id="4cd5f-206">csharp_prefer_simple_using_statement</span><span class="sxs-lookup"><span data-stu-id="4cd5f-206">csharp_prefer_simple_using_statement</span></span>](ide0063.md#csharp_prefer_simple_using_statement)
- [<span data-ttu-id="4cd5f-207">' Using ' yönerge tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-207">'using' directive preferences</span></span>](ide0065.md)
  - [<span data-ttu-id="4cd5f-208">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="4cd5f-208">csharp_using_directive_placement</span></span>](ide0065.md#csharp_using_directive_placement)
- [<span data-ttu-id="4cd5f-209">Değiştirici tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-209">Modifier preferences</span></span>](modifier-preferences.md#c-modifier-preferences)
  - [<span data-ttu-id="4cd5f-210">csharp_prefer_static_local_function</span><span class="sxs-lookup"><span data-stu-id="4cd5f-210">csharp_prefer_static_local_function</span></span>](ide0062.md#csharp_prefer_static_local_function)
  - <span data-ttu-id="4cd5f-211">[Struct alanlarını yazılabilir yap](ide0064.md) -bu kuralda kod stili seçeneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-211">[Make struct fields writable](ide0064.md) - This rule has no code style option.</span></span>

## <a name="visual-basic-style-rules"></a><span data-ttu-id="4cd5f-212">Visual Basic stil kuralları</span><span class="sxs-lookup"><span data-stu-id="4cd5f-212">Visual Basic style rules</span></span>

<span data-ttu-id="4cd5f-213">Bu bölümdeki stil kuralları yalnızca Visual Basic dil için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-213">The style rules in this section are applicable to Visual Basic language only.</span></span>

- [<span data-ttu-id="4cd5f-214">Desen eşleştirme tercihleri</span><span class="sxs-lookup"><span data-stu-id="4cd5f-214">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="4cd5f-215">visual_basic_style_prefer_isnot_expression</span><span class="sxs-lookup"><span data-stu-id="4cd5f-215">visual_basic_style_prefer_isnot_expression</span></span>](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a><span data-ttu-id="4cd5f-216">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cd5f-216">See also</span></span>

- [<span data-ttu-id="4cd5f-217">Gereksiz kod kuralları</span><span class="sxs-lookup"><span data-stu-id="4cd5f-217">Unnecessary code rules</span></span>](unnecessary-code-rules.md)
- [<span data-ttu-id="4cd5f-218">Biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="4cd5f-218">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="4cd5f-219">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="4cd5f-219">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="4cd5f-220">.NET kod stili kuralları başvurusu</span><span class="sxs-lookup"><span data-stu-id="4cd5f-220">.NET code style rules reference</span></span>](index.md)
