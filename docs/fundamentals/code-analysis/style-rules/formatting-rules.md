---
title: Kod stili biçimlendirme kuralları
description: Girintileri, boşlukları ve yeni satırları biçimlendirmeye yönelik kod stili kuralları hakkında bilgi edinin.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE0055
- formatting rules
helpviewer_keywords:
- IDE0055
- formatting code style rules [EditorConfig]
- formatting rules
- EditorConfig formatting conventions
ms.openlocfilehash: 866949692341f65a5b78c7dd5b8eec918873d3b7
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511807"
---
# <a name="formatting-rules"></a><span data-ttu-id="34fe1-103">Biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="34fe1-103">Formatting rules</span></span>

<span data-ttu-id="34fe1-104">Biçimlendirme kuralları, girintileme, boşluklar ve yeni satırların .NET programlama dili yapıları etrafında nasıl hizalanacağını etkiler.</span><span class="sxs-lookup"><span data-stu-id="34fe1-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="34fe1-105">Kurallar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="34fe1-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="34fe1-106">[.NET biçimlendirme kuralları](#net-formatting-rules): hem C# hem de Visual Basic için uygulanan kurallar.</span><span class="sxs-lookup"><span data-stu-id="34fe1-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="34fe1-107">Bu kuralların EditorConfig seçenek adları `dotnet_` ön Ekle başlar.</span><span class="sxs-lookup"><span data-stu-id="34fe1-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="34fe1-108">[C# biçimlendirme kuralları](#c-formatting-rules): yalnızca c# diline özgü kurallardır.</span><span class="sxs-lookup"><span data-stu-id="34fe1-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="34fe1-109">Bu kuralların EditorConfig seçenek adları `csharp_` ön Ekle başlar.</span><span class="sxs-lookup"><span data-stu-id="34fe1-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="34fe1-110">Kural KIMLIĞI: "IDE0055" (biçimlendirmeyi çözme)</span><span class="sxs-lookup"><span data-stu-id="34fe1-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="34fe1-111">Tüm biçimlendirme seçeneklerinde kural KIMLIĞI `IDE0055` ve başlık vardır `Fix formatting` .</span><span class="sxs-lookup"><span data-stu-id="34fe1-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="34fe1-112">Aşağıdaki yapılandırma satırını kullanarak bir EditorConfig dosyasındaki biçimlendirme ihlalinin önem derecesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="34fe1-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="34fe1-113">Önem derecesi değeri, `warning` `error` [derleme üzerinde zorlanmalıdır](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="34fe1-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="34fe1-114">Tüm olası önem derecesi değerleri için bkz. [önem düzeyi](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="34fe1-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="34fe1-115">Seçenek biçimi</span><span class="sxs-lookup"><span data-stu-id="34fe1-115">Option format</span></span>

<span data-ttu-id="34fe1-116">Biçimlendirme kuralları için seçenekler bir EditorConfig dosyasında aşağıdaki biçimde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="34fe1-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="34fe1-117">Birçok kural için `true` (Bu stili tercih et) veya `false` (Bu stili tercih etme) için bir tane belirtin `value` .</span><span class="sxs-lookup"><span data-stu-id="34fe1-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="34fe1-118">Diğer kurallar için, `flush_left` ya da `before_and_after` kuralın ne zaman ve nereye uygulanacağını betimleyen bir değer belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34fe1-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="34fe1-119">Önem derecesi belirtmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="34fe1-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="34fe1-120">.NET biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="34fe1-120">.NET formatting rules</span></span>

<span data-ttu-id="34fe1-121">Bu bölümdeki biçimlendirme kuralları hem C# hem de Visual Basic için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="34fe1-122">Using deyimlerini Düzenle</span><span class="sxs-lookup"><span data-stu-id="34fe1-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="34fe1-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="34fe1-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="34fe1-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="34fe1-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="34fe1-125">Yönergeleri kullanarak düzenleme</span><span class="sxs-lookup"><span data-stu-id="34fe1-125">Organize using directives</span></span>

<span data-ttu-id="34fe1-126">Bu biçimlendirme kuralları yönergeleri ve deyimleri sıralamayı ve görüntülemeyi sorun `using` `Imports` .</span><span class="sxs-lookup"><span data-stu-id="34fe1-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="34fe1-127">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="34fe1-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="34fe1-128">DotNet \_ sıralama \_ sistem \_ directives_first</span><span class="sxs-lookup"><span data-stu-id="34fe1-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="34fe1-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-129">Property</span></span>|<span data-ttu-id="34fe1-130">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-130">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-131">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-131">**Option name**</span></span> | <span data-ttu-id="34fe1-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="34fe1-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="34fe1-133">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-133">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-134">C# ve Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34fe1-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="34fe1-135">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-135">**Introduced version**</span></span> | <span data-ttu-id="34fe1-136">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-137">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-137">**Option values**</span></span> | <span data-ttu-id="34fe1-138">`true` - `System.*` `using` Yönergeleri alfabetik olarak sıralayın ve diğer using yönergelerinden önce yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="34fe1-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="34fe1-139">`false` - `System.*` `using` Yönergeleri diğer yönergelerden önce yerleştirmeyin `using` .</span><span class="sxs-lookup"><span data-stu-id="34fe1-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="34fe1-140">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-140">Code examples:</span></span>

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="34fe1-141">DotNet \_ ayrı \_ içeri aktarma \_ yönergesi \_ grupları</span><span class="sxs-lookup"><span data-stu-id="34fe1-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="34fe1-142">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-142">Property</span></span>|<span data-ttu-id="34fe1-143">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-143">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-144">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-144">**Option name**</span></span> | <span data-ttu-id="34fe1-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="34fe1-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="34fe1-146">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-146">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-147">C# ve Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34fe1-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="34fe1-148">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-148">**Introduced version**</span></span> | <span data-ttu-id="34fe1-149">Visual Studio 2017 sürüm 15.5</span><span class="sxs-lookup"><span data-stu-id="34fe1-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="34fe1-150">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-150">**Option values**</span></span> | <span data-ttu-id="34fe1-151">`true` -Yönerge grupları arasına boş bir satır koyun `using` .</span><span class="sxs-lookup"><span data-stu-id="34fe1-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="34fe1-152">`false` -Yönerge grupları arasına boş bir satır yerleştirmeyin `using` .</span><span class="sxs-lookup"><span data-stu-id="34fe1-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="34fe1-153">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-153">Code examples:</span></span>

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-rules"></a><span data-ttu-id="34fe1-154">C# biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="34fe1-154">C# formatting rules</span></span>

<span data-ttu-id="34fe1-155">Bu bölümdeki biçimlendirme kuralları yalnızca C# kodu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="34fe1-156">Yeni satır seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="34fe1-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="34fe1-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="34fe1-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="34fe1-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="34fe1-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="34fe1-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="34fe1-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="34fe1-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="34fe1-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="34fe1-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="34fe1-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="34fe1-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="34fe1-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="34fe1-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="34fe1-164">Girintileme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="34fe1-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="34fe1-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="34fe1-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="34fe1-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="34fe1-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="34fe1-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="34fe1-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="34fe1-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="34fe1-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="34fe1-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="34fe1-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="34fe1-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="34fe1-171">Aralık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="34fe1-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="34fe1-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="34fe1-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="34fe1-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="34fe1-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="34fe1-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="34fe1-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="34fe1-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="34fe1-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="34fe1-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="34fe1-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="34fe1-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="34fe1-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="34fe1-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="34fe1-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="34fe1-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="34fe1-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="34fe1-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="34fe1-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="34fe1-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="34fe1-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="34fe1-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="34fe1-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="34fe1-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="34fe1-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="34fe1-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="34fe1-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="34fe1-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="34fe1-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="34fe1-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="34fe1-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="34fe1-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="34fe1-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="34fe1-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="34fe1-194">Sarlama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="34fe1-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="34fe1-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="34fe1-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="34fe1-197">Yönerge seçeneklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="34fe1-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="34fe1-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="34fe1-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="34fe1-199">Yeni satır seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-199">New-line options</span></span>

<span data-ttu-id="34fe1-200">Bu biçimlendirme kuralları kodu biçimlendirmek için yeni satırların kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="34fe1-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="34fe1-201">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="34fe1-201">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="34fe1-202">\_ \_ \_ open_brace önce CSharp yeni \_ satırı</span><span class="sxs-lookup"><span data-stu-id="34fe1-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="34fe1-203">Bu kural, bir açık küme ayracın `{` önceki kodla aynı satıra mi yoksa yeni bir satıra mı yerleştirileceğini ele alır.</span><span class="sxs-lookup"><span data-stu-id="34fe1-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="34fe1-204">Bu kural için, bu kuralın ne zaman uygulanacağını tanımlamak üzere **Yöntemler** veya **Özellikler** gibi **All**, **none** veya bir ya da daha fazla kod öğesi belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34fe1-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="34fe1-205">Birden çok kod öğesi belirtmek için bunları virgülle (,) ayırın.</span><span class="sxs-lookup"><span data-stu-id="34fe1-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="34fe1-206">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-206">Property</span></span>|<span data-ttu-id="34fe1-207">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-207">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-208">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-208">**Option name**</span></span> | <span data-ttu-id="34fe1-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="34fe1-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="34fe1-210">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-210">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-211">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-211">C#</span></span> |
| <span data-ttu-id="34fe1-212">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-212">**Introduced version**</span></span> | <span data-ttu-id="34fe1-213">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-214">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-214">**Option values**</span></span> | <span data-ttu-id="34fe1-215">`all` -Küme ayracın tüm ifadeler için yeni bir satırda olması gerekir ("Allman" stili).</span><span class="sxs-lookup"><span data-stu-id="34fe1-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="34fe1-216">`none` -Küme ayracın tüm ifadeler için aynı satırda olması gerekir ("K&R").</span><span class="sxs-lookup"><span data-stu-id="34fe1-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="34fe1-217">`accessors`, `anonymous_methods` , `anonymous_types` , `control_blocks` , `events` , `indexers` , `lambdas` , `local_functions` , `methods` , `object_collection_array_initializers` , `properties` , `types` -Küme ayracı belirtilen kod öğesi ("Allman" stili) için yeni bir satırda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="34fe1-218">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-218">Code examples:</span></span>

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="34fe1-219">CSharp \_ Yeni \_ satır \_ before_else</span><span class="sxs-lookup"><span data-stu-id="34fe1-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="34fe1-220">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-220">Property</span></span>|<span data-ttu-id="34fe1-221">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-221">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-222">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-222">**Option name**</span></span> | <span data-ttu-id="34fe1-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="34fe1-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="34fe1-224">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-224">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-225">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-225">C#</span></span> |
| <span data-ttu-id="34fe1-226">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-226">**Introduced version**</span></span> | <span data-ttu-id="34fe1-227">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-228">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-228">**Option values**</span></span> | <span data-ttu-id="34fe1-229">`true` - `else` Deyimlerini yeni bir satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="34fe1-230">`false` - `else` Deyimleri aynı satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="34fe1-231">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-231">Code examples:</span></span>

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="34fe1-232">CSharp \_ Yeni \_ satır \_ before_catch</span><span class="sxs-lookup"><span data-stu-id="34fe1-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="34fe1-233">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-233">Property</span></span>|<span data-ttu-id="34fe1-234">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-234">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-235">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-235">**Option name**</span></span> | <span data-ttu-id="34fe1-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="34fe1-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="34fe1-237">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-237">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-238">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-238">C#</span></span> |
| <span data-ttu-id="34fe1-239">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-239">**Introduced version**</span></span> | <span data-ttu-id="34fe1-240">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-241">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-241">**Option values**</span></span> | <span data-ttu-id="34fe1-242">`true` - `catch` Deyimlerini yeni bir satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="34fe1-243">`false` - `catch` Deyimleri aynı satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="34fe1-244">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-244">Code examples:</span></span>

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="34fe1-245">CSharp \_ Yeni \_ satır \_ before_finally</span><span class="sxs-lookup"><span data-stu-id="34fe1-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="34fe1-246">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-246">Property</span></span>|<span data-ttu-id="34fe1-247">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-247">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-248">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-248">**Option name**</span></span> | <span data-ttu-id="34fe1-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="34fe1-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="34fe1-250">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-250">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-251">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-251">C#</span></span> |
| <span data-ttu-id="34fe1-252">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-252">**Introduced version**</span></span> | <span data-ttu-id="34fe1-253">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-254">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-254">**Option values**</span></span> | <span data-ttu-id="34fe1-255">`true` - `finally` Deyimlerin, kapanış ayracından sonra yeni bir satırda olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="34fe1-256">`false` - `finally` Deyimlerinin kapanış ayracı ile aynı satırda olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="34fe1-257">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-257">Code examples:</span></span>

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="34fe1-258">\_ \_ \_ \_ object_initializers üyelerinizden önce \_ CSharp yeni \_ satır</span><span class="sxs-lookup"><span data-stu-id="34fe1-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="34fe1-259">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-259">Property</span></span>|<span data-ttu-id="34fe1-260">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-260">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-261">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-261">**Option name**</span></span> | <span data-ttu-id="34fe1-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="34fe1-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="34fe1-263">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-263">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-264">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-264">C#</span></span> |
| <span data-ttu-id="34fe1-265">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-265">**Introduced version**</span></span> | <span data-ttu-id="34fe1-266">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-267">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-267">**Option values**</span></span> | <span data-ttu-id="34fe1-268">`true` -Nesne başlatıcılarının üyelerinin ayrı satırlarda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="34fe1-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="34fe1-269">`false` -Nesne başlatıcılarının üyelerinin aynı satırda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="34fe1-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="34fe1-270">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-270">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="34fe1-271">\_ \_ \_ \_ anonymous_types üyelerinizden önce \_ CSharp yeni \_ satır</span><span class="sxs-lookup"><span data-stu-id="34fe1-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="34fe1-272">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-272">Property</span></span>|<span data-ttu-id="34fe1-273">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-273">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-274">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-274">**Option name**</span></span> | <span data-ttu-id="34fe1-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="34fe1-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="34fe1-276">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-276">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-277">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-277">C#</span></span> |
| <span data-ttu-id="34fe1-278">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-278">**Introduced version**</span></span> | <span data-ttu-id="34fe1-279">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-280">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-280">**Option values**</span></span> | <span data-ttu-id="34fe1-281">`true` -Anonim türlerin üyelerinin ayrı satırlarda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="34fe1-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="34fe1-282">`false` -Anonim türlerin üyelerinin aynı satırda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="34fe1-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="34fe1-283">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-283">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="34fe1-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="34fe1-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="34fe1-285">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-285">Property</span></span>|<span data-ttu-id="34fe1-286">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-286">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-287">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-287">**Option name**</span></span> | <span data-ttu-id="34fe1-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="34fe1-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="34fe1-289">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-289">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-290">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-290">C#</span></span> |
| <span data-ttu-id="34fe1-291">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-291">**Introduced version**</span></span> | <span data-ttu-id="34fe1-292">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-293">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-293">**Option values**</span></span> | <span data-ttu-id="34fe1-294">`true` -Sorgu ifadesi yan tümcelerinin öğelerinin ayrı satırlarda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="34fe1-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="34fe1-295">`false` -Sorgu ifadesi yan tümcelerinin öğelerin aynı satırda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="34fe1-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="34fe1-296">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="34fe1-297">Girintileme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-297">Indentation options</span></span>

<span data-ttu-id="34fe1-298">Bu biçimlendirme kuralları kodu biçimlendirmek için girintileme kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="34fe1-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="34fe1-299">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="34fe1-299">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="34fe1-300">CSharp \_ girintileme \_ case_contents</span><span class="sxs-lookup"><span data-stu-id="34fe1-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="34fe1-301">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-301">Property</span></span>|<span data-ttu-id="34fe1-302">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-302">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-303">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-303">**Option name**</span></span> | <span data-ttu-id="34fe1-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="34fe1-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="34fe1-305">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-305">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-306">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-306">C#</span></span> |
| <span data-ttu-id="34fe1-307">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-307">**Introduced version**</span></span> | <span data-ttu-id="34fe1-308">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-309">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-309">**Option values**</span></span> | <span data-ttu-id="34fe1-310">`true` - `switch` Case içeriğini Girintile</span><span class="sxs-lookup"><span data-stu-id="34fe1-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="34fe1-311">`false` - `switch` Servis talebi içeriklerini girintileme</span><span class="sxs-lookup"><span data-stu-id="34fe1-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="34fe1-312">Bu kural **true** olarak ayarlandığında, ı.</span><span class="sxs-lookup"><span data-stu-id="34fe1-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="34fe1-313">Bu kural **false**, d olarak ayarlandığında.</span><span class="sxs-lookup"><span data-stu-id="34fe1-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="34fe1-314">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-314">Code examples:</span></span>

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="34fe1-315">CSharp \_ girintileme \_ switch_labels</span><span class="sxs-lookup"><span data-stu-id="34fe1-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="34fe1-316">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-316">Property</span></span>|<span data-ttu-id="34fe1-317">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-317">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-318">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-318">**Option name**</span></span> | <span data-ttu-id="34fe1-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="34fe1-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="34fe1-320">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-320">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-321">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-321">C#</span></span> |
| <span data-ttu-id="34fe1-322">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-322">**Introduced version**</span></span> | <span data-ttu-id="34fe1-323">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-324">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-324">**Option values**</span></span> | <span data-ttu-id="34fe1-325">`true` - `switch` Etiketleri Girintile</span><span class="sxs-lookup"><span data-stu-id="34fe1-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="34fe1-326">`false` - `switch` Etiketleri girintileme</span><span class="sxs-lookup"><span data-stu-id="34fe1-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="34fe1-327">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-327">Code examples:</span></span>

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a><span data-ttu-id="34fe1-328">CSharp \_ indent_labels</span><span class="sxs-lookup"><span data-stu-id="34fe1-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="34fe1-329">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-329">Property</span></span>|<span data-ttu-id="34fe1-330">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-330">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-331">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-331">**Option name**</span></span> | <span data-ttu-id="34fe1-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="34fe1-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="34fe1-333">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-333">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-334">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-334">C#</span></span> |
| <span data-ttu-id="34fe1-335">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-335">**Introduced version**</span></span> | <span data-ttu-id="34fe1-336">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-337">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-337">**Option values**</span></span> | <span data-ttu-id="34fe1-338">`flush_left` -Etiketler en soldaki sütuna yerleştirilir</span><span class="sxs-lookup"><span data-stu-id="34fe1-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="34fe1-339">`one_less_than_current` -Etiketler geçerli bağlama göre daha az bir girintide yerleştirilir</span><span class="sxs-lookup"><span data-stu-id="34fe1-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="34fe1-340">`no_change` -Etiketler, geçerli bağlamla aynı girintide yer alır</span><span class="sxs-lookup"><span data-stu-id="34fe1-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="34fe1-341">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-341">Code examples:</span></span>

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="34fe1-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="34fe1-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="34fe1-343">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-343">Property</span></span>|<span data-ttu-id="34fe1-344">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-344">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-345">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-345">**Option name**</span></span> | <span data-ttu-id="34fe1-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="34fe1-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="34fe1-347">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-347">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-348">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-348">C#</span></span> |
| <span data-ttu-id="34fe1-349">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="34fe1-350">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-350">Code examples:</span></span>

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a><span data-ttu-id="34fe1-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="34fe1-351">csharp_indent_braces</span></span>

|<span data-ttu-id="34fe1-352">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-352">Property</span></span>|<span data-ttu-id="34fe1-353">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-353">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-354">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-354">**Option name**</span></span> | <span data-ttu-id="34fe1-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="34fe1-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="34fe1-356">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-356">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-357">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-357">C#</span></span> |
| <span data-ttu-id="34fe1-358">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="34fe1-359">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-359">Code examples:</span></span>

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="34fe1-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="34fe1-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="34fe1-361">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-361">Property</span></span>|<span data-ttu-id="34fe1-362">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-362">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-363">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-363">**Option name**</span></span> | <span data-ttu-id="34fe1-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="34fe1-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="34fe1-365">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-365">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-366">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-366">C#</span></span> |
| <span data-ttu-id="34fe1-367">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="34fe1-368">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-368">Code examples:</span></span>

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a><span data-ttu-id="34fe1-369">Aralık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-369">Spacing options</span></span>

<span data-ttu-id="34fe1-370">Bu biçimlendirme kuralları kodu biçimlendirmek için boşluk karakterlerinin kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="34fe1-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="34fe1-371">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="34fe1-371">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="34fe1-372">CSharp \_ space \_ after_cast</span><span class="sxs-lookup"><span data-stu-id="34fe1-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="34fe1-373">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-373">Property</span></span>|<span data-ttu-id="34fe1-374">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-374">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-375">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-375">**Option name**</span></span> | <span data-ttu-id="34fe1-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="34fe1-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="34fe1-377">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-377">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-378">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-378">C#</span></span> |
| <span data-ttu-id="34fe1-379">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-379">**Introduced version**</span></span> | <span data-ttu-id="34fe1-380">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-381">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-381">**Option values**</span></span> | <span data-ttu-id="34fe1-382">`true` -Bir atama ve değer arasına bir boşluk karakteri koyun</span><span class="sxs-lookup"><span data-stu-id="34fe1-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="34fe1-383">`false` -Cast ve değer arasındaki boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="34fe1-384">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="34fe1-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="34fe1-386">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-386">Property</span></span>|<span data-ttu-id="34fe1-387">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-387">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-388">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-388">**Option name**</span></span> | <span data-ttu-id="34fe1-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="34fe1-390">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-390">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-391">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-391">C#</span></span> |
| <span data-ttu-id="34fe1-392">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-392">**Introduced version**</span></span> | <span data-ttu-id="34fe1-393">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-394">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-394">**Option values**</span></span> | <span data-ttu-id="34fe1-395">`true`-Döngü gibi bir denetim akışı deyimindeki anahtar sözcükten sonra bir boşluk karakteri yerleştir `for`</span><span class="sxs-lookup"><span data-stu-id="34fe1-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="34fe1-396">`false`-Döngü gibi bir denetim akışı deyimindeki anahtar sözcükten sonra boşluk Kaldır `for`</span><span class="sxs-lookup"><span data-stu-id="34fe1-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="34fe1-397">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="34fe1-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="34fe1-399">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-399">Property</span></span>|<span data-ttu-id="34fe1-400">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-400">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-401">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-401">**Option name**</span></span> | <span data-ttu-id="34fe1-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="34fe1-403">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-403">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-404">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-404">C#</span></span> |
| <span data-ttu-id="34fe1-405">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-405">**Introduced version**</span></span> | <span data-ttu-id="34fe1-406">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-407">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-407">**Option values**</span></span> | <span data-ttu-id="34fe1-408">`control_flow_statements` -Denetim akışı deyimlerinin parantezleri arasına boşluk yerleştir</span><span class="sxs-lookup"><span data-stu-id="34fe1-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="34fe1-409">`expressions` -İfadelerin parantezleri arasına boşluk yerleştir</span><span class="sxs-lookup"><span data-stu-id="34fe1-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="34fe1-410">`type_casts` -Tür atamalerdeki parantezler arasında boşluk yerleştir</span><span class="sxs-lookup"><span data-stu-id="34fe1-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="34fe1-411">Bu kuralı atlarsanız veya,, veya dışında bir değer kullanırsanız `control_flow_statements` , `expressions` `type_casts` ayar uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="34fe1-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="34fe1-412">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="34fe1-413">\_ \_ \_ inheritance_clause iki noktadan önce \_ CSharp \_ Space</span><span class="sxs-lookup"><span data-stu-id="34fe1-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="34fe1-414">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-414">Property</span></span>|<span data-ttu-id="34fe1-415">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-415">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-416">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-416">**Option name**</span></span> | <span data-ttu-id="34fe1-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="34fe1-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="34fe1-418">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-418">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-419">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-419">C#</span></span> |
| <span data-ttu-id="34fe1-420">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-420">**Introduced version**</span></span> | <span data-ttu-id="34fe1-421">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="34fe1-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="34fe1-422">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-422">**Option values**</span></span> | <span data-ttu-id="34fe1-423">`true` -Bir tür bildiriminde temeller veya arabirimler için iki noktadan önce bir boşluk karakteri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="34fe1-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="34fe1-424">`false` -Tür bildiriminde temeller veya arabirimler için iki noktadan önce boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="34fe1-425">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-425">Code examples:</span></span>

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="34fe1-426">\_ \_ \_ inheritance_clause iki noktadan sonra \_ CSharp \_ Space</span><span class="sxs-lookup"><span data-stu-id="34fe1-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="34fe1-427">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-427">Property</span></span>|<span data-ttu-id="34fe1-428">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-428">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-429">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-429">**Option name**</span></span> | <span data-ttu-id="34fe1-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="34fe1-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="34fe1-431">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-431">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-432">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-432">C#</span></span> |
| <span data-ttu-id="34fe1-433">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-433">**Introduced version**</span></span> | <span data-ttu-id="34fe1-434">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="34fe1-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="34fe1-435">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-435">**Option values**</span></span> | <span data-ttu-id="34fe1-436">`true` -Bir tür bildiriminde tabanların veya arabirimlerin iki noktadan sonra bir boşluk karakteri yerleştir</span><span class="sxs-lookup"><span data-stu-id="34fe1-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="34fe1-437">`false` -Bir tür bildiriminde temeller veya arabirimler için iki noktadan sonra boşluk kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="34fe1-438">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-438">Code examples:</span></span>

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="34fe1-439">\_ \_ binary_operators etrafında CSharp \_ alanı</span><span class="sxs-lookup"><span data-stu-id="34fe1-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="34fe1-440">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-440">Property</span></span>|<span data-ttu-id="34fe1-441">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-441">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-442">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-442">**Option name**</span></span> | <span data-ttu-id="34fe1-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="34fe1-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="34fe1-444">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-444">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-445">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-445">C#</span></span> |
| <span data-ttu-id="34fe1-446">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-446">**Introduced version**</span></span> | <span data-ttu-id="34fe1-447">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="34fe1-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="34fe1-448">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-448">**Option values**</span></span> | <span data-ttu-id="34fe1-449">`before_and_after` -İkili işleçten önce ve sonra boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="34fe1-450">`none` -İkili işleçten önce ve sonra boşlukları kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="34fe1-451">`ignore` -İkili operatörlerin çevresindeki boşlukları yoksay</span><span class="sxs-lookup"><span data-stu-id="34fe1-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="34fe1-452">Bu kuralı atlarsanız veya,, veya dışında bir değer kullanırsanız, `before_and_after` `none` `ignore` ayar uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="34fe1-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="34fe1-453">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="34fe1-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="34fe1-455">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-455">Property</span></span>|<span data-ttu-id="34fe1-456">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-456">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-457">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-457">**Option name**</span></span> | <span data-ttu-id="34fe1-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="34fe1-459">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-459">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-460">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-460">C#</span></span> |
| <span data-ttu-id="34fe1-461">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-461">**Introduced version**</span></span> | <span data-ttu-id="34fe1-462">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-463">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-463">**Option values**</span></span> | <span data-ttu-id="34fe1-464">`true` -Açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce bir boşluk karakteri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="34fe1-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="34fe1-465">`false` -Boşluk karakterlerini açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce kaldırın</span><span class="sxs-lookup"><span data-stu-id="34fe1-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="34fe1-466">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="34fe1-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="34fe1-468">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-468">Property</span></span>|<span data-ttu-id="34fe1-469">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-469">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-470">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-470">**Option name**</span></span> | <span data-ttu-id="34fe1-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="34fe1-472">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-472">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-473">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-473">C#</span></span> |
| <span data-ttu-id="34fe1-474">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-474">**Introduced version**</span></span> | <span data-ttu-id="34fe1-475">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="34fe1-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="34fe1-476">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-476">**Option values**</span></span> | <span data-ttu-id="34fe1-477">`true` -Yöntem bildirimi için boş parametre listesi ayraçları içine boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="34fe1-478">`false` -Yöntem bildirimi için boş parametre listesi ayraçları içindeki alanı kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="34fe1-479">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-479">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="34fe1-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="34fe1-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="34fe1-481">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-481">Property</span></span>|<span data-ttu-id="34fe1-482">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-482">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-483">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-483">**Option name**</span></span> | <span data-ttu-id="34fe1-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="34fe1-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="34fe1-485">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-485">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-486">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-486">C#</span></span> |
| <span data-ttu-id="34fe1-487">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-487">**Option values**</span></span> | <span data-ttu-id="34fe1-488">`true` -Yöntem bildiriminde Yöntem adı ve açma ayracı arasına bir boşluk karakteri koyun</span><span class="sxs-lookup"><span data-stu-id="34fe1-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="34fe1-489">`false` -Yöntem bildiriminde Yöntem adı ve açma ayracı arasındaki boşluk karakterlerini kaldırın</span><span class="sxs-lookup"><span data-stu-id="34fe1-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="34fe1-490">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="34fe1-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="34fe1-492">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-492">Property</span></span>|<span data-ttu-id="34fe1-493">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-493">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-494">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-494">**Option name**</span></span> | <span data-ttu-id="34fe1-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="34fe1-496">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-496">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-497">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-497">C#</span></span> |
| <span data-ttu-id="34fe1-498">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-498">**Introduced version**</span></span> | <span data-ttu-id="34fe1-499">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-500">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-500">**Option values**</span></span> | <span data-ttu-id="34fe1-501">`true` -Açma parantezinden sonra ve bir yöntem çağrısının kapatma parantezinden önce bir boşluk karakteri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="34fe1-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="34fe1-502">`false` -Açma parantezinden sonra ve bir yöntem çağrısının kapanış parantezinden önce boşluk karakterlerini kaldırın</span><span class="sxs-lookup"><span data-stu-id="34fe1-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="34fe1-503">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="34fe1-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="34fe1-505">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-505">Property</span></span>|<span data-ttu-id="34fe1-506">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-506">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-507">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-507">**Option name**</span></span> | <span data-ttu-id="34fe1-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="34fe1-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="34fe1-509">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-509">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-510">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-510">C#</span></span> |
| <span data-ttu-id="34fe1-511">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-511">**Introduced version**</span></span> | <span data-ttu-id="34fe1-512">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="34fe1-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="34fe1-513">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-513">**Option values**</span></span> | <span data-ttu-id="34fe1-514">`true` -Boş bağımsız değişken listesi ayraçları içine boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="34fe1-515">`false` -Boş bağımsız değişken listesi ayraçları içindeki alanı kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="34fe1-516">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-516">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="34fe1-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="34fe1-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="34fe1-518">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-518">Property</span></span>|<span data-ttu-id="34fe1-519">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-519">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-520">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-520">**Option name**</span></span> | <span data-ttu-id="34fe1-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="34fe1-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="34fe1-522">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-522">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-523">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-523">C#</span></span> |
| <span data-ttu-id="34fe1-524">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-524">**Introduced version**</span></span> | <span data-ttu-id="34fe1-525">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="34fe1-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="34fe1-526">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-526">**Option values**</span></span> | <span data-ttu-id="34fe1-527">`true` -Yöntem çağrısı adı ve açma ayracı arasına boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="34fe1-528">`false` -Yöntem çağrı adı ve açılış ayracı arasındaki boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="34fe1-529">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-529">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="34fe1-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="34fe1-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="34fe1-531">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-531">Property</span></span>|<span data-ttu-id="34fe1-532">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-532">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-533">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-533">**Option name**</span></span> | <span data-ttu-id="34fe1-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="34fe1-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="34fe1-535">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-535">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-536">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-536">C#</span></span> |
| <span data-ttu-id="34fe1-537">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-537">**Option values**</span></span> | <span data-ttu-id="34fe1-538">`true` -Virgülden sonra boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="34fe1-539">`false` -Virgülden sonra boşluk kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="34fe1-540">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="34fe1-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="34fe1-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="34fe1-542">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-542">Property</span></span>|<span data-ttu-id="34fe1-543">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-543">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-544">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-544">**Option name**</span></span> | <span data-ttu-id="34fe1-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="34fe1-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="34fe1-546">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-546">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-547">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-547">C#</span></span> |
| <span data-ttu-id="34fe1-548">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-548">**Option values**</span></span> | <span data-ttu-id="34fe1-549">`true` -Virgülden önce boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="34fe1-550">`false` -Bir virgülden önce boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="34fe1-551">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="34fe1-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="34fe1-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="34fe1-553">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-553">Property</span></span>|<span data-ttu-id="34fe1-554">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-554">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-555">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-555">**Option name**</span></span> | <span data-ttu-id="34fe1-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="34fe1-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="34fe1-557">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-557">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-558">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-558">C#</span></span> |
| <span data-ttu-id="34fe1-559">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-559">**Option values**</span></span> | <span data-ttu-id="34fe1-560">`true` -Noktadan sonra boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="34fe1-561">`false` -Noktadan sonra boşluk kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="34fe1-562">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="34fe1-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="34fe1-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="34fe1-564">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-564">Property</span></span>|<span data-ttu-id="34fe1-565">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-565">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-566">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-566">**Option name**</span></span> | <span data-ttu-id="34fe1-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="34fe1-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="34fe1-568">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-568">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-569">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-569">C#</span></span> |
| <span data-ttu-id="34fe1-570">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-570">**Option values**</span></span> | <span data-ttu-id="34fe1-571">`true` -Noktadan önce boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="34fe1-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="34fe1-572">`false` -Noktadan önce boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="34fe1-573">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="34fe1-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="34fe1-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="34fe1-575">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-575">Property</span></span>|<span data-ttu-id="34fe1-576">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-576">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-577">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-577">**Option name**</span></span> | <span data-ttu-id="34fe1-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="34fe1-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="34fe1-579">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-579">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-580">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-580">C#</span></span> |
| <span data-ttu-id="34fe1-581">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-581">**Option values**</span></span> | <span data-ttu-id="34fe1-582">`true`-Bir ifadede her noktalı virgülden sonra boşluk Ekle `for`</span><span class="sxs-lookup"><span data-stu-id="34fe1-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="34fe1-583">`false`-Bir bildirimde her noktalı virgülden sonra boşluk Kaldır `for`</span><span class="sxs-lookup"><span data-stu-id="34fe1-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="34fe1-584">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

#### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="34fe1-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="34fe1-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="34fe1-586">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-586">Property</span></span>|<span data-ttu-id="34fe1-587">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-587">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-588">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-588">**Option name**</span></span> | <span data-ttu-id="34fe1-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="34fe1-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="34fe1-590">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-590">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-591">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-591">C#</span></span> |
| <span data-ttu-id="34fe1-592">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-592">**Option values**</span></span> | <span data-ttu-id="34fe1-593">`true`-Bir bildirimde her noktalı virgülden önce boşluk Ekle `for`</span><span class="sxs-lookup"><span data-stu-id="34fe1-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="34fe1-594">`false`-Bir bildirimde her noktalı virgülden önce boşluk Kaldır `for`</span><span class="sxs-lookup"><span data-stu-id="34fe1-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="34fe1-595">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="34fe1-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="34fe1-597">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-597">Property</span></span>|<span data-ttu-id="34fe1-598">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-598">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-599">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-599">**Option name**</span></span> | <span data-ttu-id="34fe1-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="34fe1-601">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-601">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-602">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-602">C#</span></span> |
| <span data-ttu-id="34fe1-603">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-603">**Option values**</span></span> | <span data-ttu-id="34fe1-604">`ignore` -Bildirim deyimlerine fazladan boşluk karakterleri kaldırmayın</span><span class="sxs-lookup"><span data-stu-id="34fe1-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="34fe1-605">`false` -Bildirim deyimlerine ek boşluk karakterlerini kaldır</span><span class="sxs-lookup"><span data-stu-id="34fe1-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="34fe1-606">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="34fe1-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="34fe1-608">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-608">Property</span></span>|<span data-ttu-id="34fe1-609">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-609">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-610">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-610">**Option name**</span></span> | <span data-ttu-id="34fe1-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="34fe1-612">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-612">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-613">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-613">C#</span></span> |
| <span data-ttu-id="34fe1-614">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-614">**Option values**</span></span> | <span data-ttu-id="34fe1-615">`true` -Açılış köşeli ayracından önce boşluk Ekle `[`</span><span class="sxs-lookup"><span data-stu-id="34fe1-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="34fe1-616">`false` -Köşeli ayraçları açmadan önce boşluğu kaldır `[`</span><span class="sxs-lookup"><span data-stu-id="34fe1-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="34fe1-617">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="34fe1-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="34fe1-619">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-619">Property</span></span>|<span data-ttu-id="34fe1-620">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-620">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-621">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-621">**Option name**</span></span> | <span data-ttu-id="34fe1-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="34fe1-623">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-623">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-624">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-624">C#</span></span> |
| <span data-ttu-id="34fe1-625">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-625">**Option values**</span></span> | <span data-ttu-id="34fe1-626">`true` -Boş köşeli ayraç arasına boşluk Ekle `[ ]`</span><span class="sxs-lookup"><span data-stu-id="34fe1-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="34fe1-627">`false` -Boş köşeli ayraçlar arasındaki boşluğu kaldır `[]`</span><span class="sxs-lookup"><span data-stu-id="34fe1-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="34fe1-628">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="34fe1-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="34fe1-630">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-630">Property</span></span>|<span data-ttu-id="34fe1-631">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-631">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-632">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-632">**Option name**</span></span> | <span data-ttu-id="34fe1-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="34fe1-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="34fe1-634">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-634">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-635">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-635">C#</span></span> |
| <span data-ttu-id="34fe1-636">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-636">**Option values**</span></span> | <span data-ttu-id="34fe1-637">`true` -Boş olmayan köşeli Parantezde boşluk karakterleri Ekle `[ 0 ]`</span><span class="sxs-lookup"><span data-stu-id="34fe1-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="34fe1-638">`false` -Boş olmayan köşeli ayraçdaki boşluk karakterlerini kaldır `[0]`</span><span class="sxs-lookup"><span data-stu-id="34fe1-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="34fe1-639">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="34fe1-640">Sarlama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34fe1-640">Wrap options</span></span>

<span data-ttu-id="34fe1-641">Bu biçimlendirme kuralları, deyimler ve kod blokları için ayrı satırlara karşı tek satırların kullanımını önemli olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="34fe1-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="34fe1-642">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="34fe1-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="34fe1-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="34fe1-644">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-644">Property</span></span>|<span data-ttu-id="34fe1-645">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-645">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-646">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-646">**Option name**</span></span> | <span data-ttu-id="34fe1-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="34fe1-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="34fe1-648">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-648">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-649">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-649">C#</span></span> |
| <span data-ttu-id="34fe1-650">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-650">**Introduced version**</span></span> | <span data-ttu-id="34fe1-651">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-652">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-652">**Option values**</span></span> | <span data-ttu-id="34fe1-653">`true` -Deyimleri ve üye bildirimlerini aynı satırda bırak</span><span class="sxs-lookup"><span data-stu-id="34fe1-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="34fe1-654">`false` -Deyimleri ve üye bildirimlerini farklı satırlarda bırak</span><span class="sxs-lookup"><span data-stu-id="34fe1-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="34fe1-655">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="34fe1-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="34fe1-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="34fe1-657">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-657">Property</span></span>|<span data-ttu-id="34fe1-658">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-658">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-659">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-659">**Option name**</span></span> | <span data-ttu-id="34fe1-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="34fe1-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="34fe1-661">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-661">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-662">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-662">C#</span></span> |
| <span data-ttu-id="34fe1-663">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-663">**Introduced version**</span></span> | <span data-ttu-id="34fe1-664">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="34fe1-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="34fe1-665">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-665">**Option values**</span></span> | <span data-ttu-id="34fe1-666">`true` -Kod bloğunu tek satırda bırak</span><span class="sxs-lookup"><span data-stu-id="34fe1-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="34fe1-667">`false` -Kod bloğunu ayrı satırlarda bırak</span><span class="sxs-lookup"><span data-stu-id="34fe1-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="34fe1-668">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="34fe1-669">Yönerge seçeneklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="34fe1-669">Using directive options</span></span>

<span data-ttu-id="34fe1-670">Bu biçimlendirme kuralı, bir ad alanı dışında, içine yerleştirilmiş yönergelerin kullanımı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="34fe1-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="34fe1-671">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="34fe1-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="34fe1-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="34fe1-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="34fe1-673">Özellik</span><span class="sxs-lookup"><span data-stu-id="34fe1-673">Property</span></span>|<span data-ttu-id="34fe1-674">Değer</span><span class="sxs-lookup"><span data-stu-id="34fe1-674">Value</span></span>|
|-|-|
| <span data-ttu-id="34fe1-675">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="34fe1-675">**Option name**</span></span> | <span data-ttu-id="34fe1-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="34fe1-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="34fe1-677">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="34fe1-677">**Applicable languages**</span></span> | <span data-ttu-id="34fe1-678">C#</span><span class="sxs-lookup"><span data-stu-id="34fe1-678">C#</span></span> |
| <span data-ttu-id="34fe1-679">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="34fe1-679">**Introduced version**</span></span> | <span data-ttu-id="34fe1-680"> Visual Studio 2019 sürüm 16.1</span><span class="sxs-lookup"><span data-stu-id="34fe1-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="34fe1-681">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="34fe1-681">**Option values**</span></span> | <span data-ttu-id="34fe1-682">`outside_namespace` -Ad alanı dışındaki yönergeleri kullanmayı bırak</span><span class="sxs-lookup"><span data-stu-id="34fe1-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="34fe1-683">`inside_namespace` -Ad alanı içinde yönergeleri kullanmayı bırak</span><span class="sxs-lookup"><span data-stu-id="34fe1-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="34fe1-684">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="34fe1-684">Code examples:</span></span>

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a><span data-ttu-id="34fe1-685">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34fe1-685">See also</span></span>

- [<span data-ttu-id="34fe1-686">Dil kuralları</span><span class="sxs-lookup"><span data-stu-id="34fe1-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="34fe1-687">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="34fe1-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="34fe1-688">.NET kod stili kuralları başvurusu</span><span class="sxs-lookup"><span data-stu-id="34fe1-688">.NET code style rules reference</span></span>](index.md)
