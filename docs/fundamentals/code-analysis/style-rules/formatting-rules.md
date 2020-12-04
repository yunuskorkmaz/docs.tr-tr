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
ms.openlocfilehash: 61e6f6a6afdc6aaf9710eef3143af8ae700ef612
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "96589393"
---
# <a name="formatting-rules"></a><span data-ttu-id="6db42-103">Biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="6db42-103">Formatting rules</span></span>

<span data-ttu-id="6db42-104">Biçimlendirme kuralları, girintileme, boşluklar ve yeni satırların .NET programlama dili yapıları etrafında nasıl hizalanacağını etkiler.</span><span class="sxs-lookup"><span data-stu-id="6db42-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="6db42-105">Kurallar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="6db42-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="6db42-106">[.NET biçimlendirme kuralları](#net-formatting-rules): hem C# hem de Visual Basic için uygulanan kurallar.</span><span class="sxs-lookup"><span data-stu-id="6db42-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="6db42-107">Bu kuralların EditorConfig seçenek adları `dotnet_` ön Ekle başlar.</span><span class="sxs-lookup"><span data-stu-id="6db42-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="6db42-108">[C# biçimlendirme kuralları](#c-formatting-rules): yalnızca c# diline özgü kurallardır.</span><span class="sxs-lookup"><span data-stu-id="6db42-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="6db42-109">Bu kuralların EditorConfig seçenek adları `csharp_` ön Ekle başlar.</span><span class="sxs-lookup"><span data-stu-id="6db42-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="6db42-110">Kural KIMLIĞI: "IDE0055" (biçimlendirmeyi çözme)</span><span class="sxs-lookup"><span data-stu-id="6db42-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="6db42-111">Tüm biçimlendirme seçeneklerinde kural KIMLIĞI `IDE0055` ve başlık vardır `Fix formatting` .</span><span class="sxs-lookup"><span data-stu-id="6db42-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="6db42-112">Aşağıdaki yapılandırma satırını kullanarak bir EditorConfig dosyasındaki biçimlendirme ihlalinin önem derecesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6db42-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="6db42-113">Önem derecesi değeri, `warning` `error` [derleme üzerinde zorlanmalıdır](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="6db42-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="6db42-114">Tüm olası önem derecesi değerleri için bkz. [önem düzeyi](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="6db42-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="6db42-115">Seçenek biçimi</span><span class="sxs-lookup"><span data-stu-id="6db42-115">Option format</span></span>

<span data-ttu-id="6db42-116">Biçimlendirme kuralları için seçenekler bir EditorConfig dosyasında aşağıdaki biçimde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="6db42-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="6db42-117">Birçok kural için `true` (Bu stili tercih et) veya `false` (Bu stili tercih etme) için bir tane belirtin `value` .</span><span class="sxs-lookup"><span data-stu-id="6db42-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="6db42-118">Diğer kurallar için, `flush_left` ya da `before_and_after` kuralın ne zaman ve nereye uygulanacağını betimleyen bir değer belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6db42-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="6db42-119">Önem derecesi belirtmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6db42-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="6db42-120">.NET biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="6db42-120">.NET formatting rules</span></span>

<span data-ttu-id="6db42-121">Bu bölümdeki biçimlendirme kuralları hem C# hem de Visual Basic için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6db42-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="6db42-122">Using deyimlerini Düzenle</span><span class="sxs-lookup"><span data-stu-id="6db42-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="6db42-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="6db42-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="6db42-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="6db42-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="6db42-125">Yönergeleri kullanarak düzenleme</span><span class="sxs-lookup"><span data-stu-id="6db42-125">Organize using directives</span></span>

<span data-ttu-id="6db42-126">Bu biçimlendirme kuralları yönergeleri ve deyimleri sıralamayı ve görüntülemeyi sorun `using` `Imports` .</span><span class="sxs-lookup"><span data-stu-id="6db42-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="6db42-127">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6db42-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="6db42-128">DotNet \_ sıralama \_ sistem \_ directives_first</span><span class="sxs-lookup"><span data-stu-id="6db42-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="6db42-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-129">Property</span></span>|<span data-ttu-id="6db42-130">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-130">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-131">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-131">**Option name**</span></span> | <span data-ttu-id="6db42-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="6db42-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="6db42-133">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-133">**Applicable languages**</span></span> | <span data-ttu-id="6db42-134">C# ve Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6db42-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="6db42-135">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-135">**Introduced version**</span></span> | <span data-ttu-id="6db42-136">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-137">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-137">**Option values**</span></span> | <span data-ttu-id="6db42-138">`true` - `System.*` `using` Yönergeleri alfabetik olarak sıralayın ve diğer using yönergelerinden önce yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6db42-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="6db42-139">`false` - `System.*` `using` Yönergeleri diğer yönergelerden önce yerleştirmeyin `using` .</span><span class="sxs-lookup"><span data-stu-id="6db42-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="6db42-140">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-140">Code examples:</span></span>

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

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="6db42-141">DotNet \_ ayrı \_ içeri aktarma \_ yönergesi \_ grupları</span><span class="sxs-lookup"><span data-stu-id="6db42-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="6db42-142">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-142">Property</span></span>|<span data-ttu-id="6db42-143">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-143">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-144">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-144">**Option name**</span></span> | <span data-ttu-id="6db42-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="6db42-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="6db42-146">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-146">**Applicable languages**</span></span> | <span data-ttu-id="6db42-147">C# ve Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6db42-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="6db42-148">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-148">**Introduced version**</span></span> | <span data-ttu-id="6db42-149">Visual Studio 2017 sürüm 15.5</span><span class="sxs-lookup"><span data-stu-id="6db42-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="6db42-150">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-150">**Option values**</span></span> | <span data-ttu-id="6db42-151">`true` -Yönerge grupları arasına boş bir satır koyun `using` .</span><span class="sxs-lookup"><span data-stu-id="6db42-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="6db42-152">`false` -Yönerge grupları arasına boş bir satır yerleştirmeyin `using` .</span><span class="sxs-lookup"><span data-stu-id="6db42-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="6db42-153">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-153">Code examples:</span></span>

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

## <a name="c-formatting-rules"></a><span data-ttu-id="6db42-154">C# biçimlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="6db42-154">C# formatting rules</span></span>

<span data-ttu-id="6db42-155">Bu bölümdeki biçimlendirme kuralları yalnızca C# kodu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6db42-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="6db42-156">Yeni satır seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="6db42-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="6db42-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="6db42-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="6db42-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="6db42-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="6db42-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="6db42-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="6db42-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="6db42-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="6db42-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="6db42-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="6db42-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="6db42-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="6db42-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="6db42-164">Girintileme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="6db42-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="6db42-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="6db42-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="6db42-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="6db42-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="6db42-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="6db42-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="6db42-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="6db42-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="6db42-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="6db42-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="6db42-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="6db42-171">Aralık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="6db42-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="6db42-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="6db42-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="6db42-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="6db42-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="6db42-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="6db42-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="6db42-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="6db42-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6db42-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="6db42-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="6db42-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="6db42-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="6db42-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="6db42-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="6db42-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="6db42-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="6db42-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="6db42-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="6db42-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="6db42-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="6db42-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="6db42-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="6db42-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="6db42-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="6db42-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="6db42-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="6db42-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="6db42-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="6db42-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="6db42-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="6db42-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="6db42-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="6db42-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="6db42-194">Sarlama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="6db42-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="6db42-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="6db42-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="6db42-197">Yönerge seçeneklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6db42-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="6db42-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="6db42-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="6db42-199">Yeni satır seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-199">New-line options</span></span>

<span data-ttu-id="6db42-200">Bu biçimlendirme kuralları kodu biçimlendirmek için yeni satırların kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6db42-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="6db42-201">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6db42-201">Example *.editorconfig* file:</span></span>

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

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="6db42-202">\_ \_ \_ open_brace önce CSharp yeni \_ satırı</span><span class="sxs-lookup"><span data-stu-id="6db42-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="6db42-203">Bu kural, bir açık küme ayracın `{` önceki kodla aynı satıra mi yoksa yeni bir satıra mı yerleştirileceğini ele alır.</span><span class="sxs-lookup"><span data-stu-id="6db42-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="6db42-204">Bu kural için, bu kuralın ne zaman uygulanacağını tanımlamak üzere **Yöntemler** veya **Özellikler** gibi **All**, **none** veya bir ya da daha fazla kod öğesi belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6db42-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="6db42-205">Birden çok kod öğesi belirtmek için bunları virgülle (,) ayırın.</span><span class="sxs-lookup"><span data-stu-id="6db42-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="6db42-206">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-206">Property</span></span>|<span data-ttu-id="6db42-207">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-207">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-208">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-208">**Option name**</span></span> | <span data-ttu-id="6db42-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="6db42-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="6db42-210">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-210">**Applicable languages**</span></span> | <span data-ttu-id="6db42-211">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-211">C#</span></span> |
| <span data-ttu-id="6db42-212">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-212">**Introduced version**</span></span> | <span data-ttu-id="6db42-213">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-214">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-214">**Option values**</span></span> | <span data-ttu-id="6db42-215">`all` -Küme ayracın tüm ifadeler için yeni bir satırda olması gerekir ("Allman" stili).</span><span class="sxs-lookup"><span data-stu-id="6db42-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="6db42-216">`none` -Küme ayracın tüm ifadeler için aynı satırda olması gerekir ("K&R").</span><span class="sxs-lookup"><span data-stu-id="6db42-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="6db42-217">`accessors`, `anonymous_methods` , `anonymous_types` , `control_blocks` , `events` , `indexers` , `lambdas` , `local_functions` , `methods` , `object_collection_array_initializers` , `properties` , `types` -Küme ayracı belirtilen kod öğesi ("Allman" stili) için yeni bir satırda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6db42-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="6db42-218">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-218">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="6db42-219">CSharp \_ Yeni \_ satır \_ before_else</span><span class="sxs-lookup"><span data-stu-id="6db42-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="6db42-220">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-220">Property</span></span>|<span data-ttu-id="6db42-221">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-221">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-222">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-222">**Option name**</span></span> | <span data-ttu-id="6db42-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="6db42-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="6db42-224">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-224">**Applicable languages**</span></span> | <span data-ttu-id="6db42-225">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-225">C#</span></span> |
| <span data-ttu-id="6db42-226">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-226">**Introduced version**</span></span> | <span data-ttu-id="6db42-227">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-228">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-228">**Option values**</span></span> | <span data-ttu-id="6db42-229">`true` - `else` Deyimlerini yeni bir satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="6db42-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="6db42-230">`false` - `else` Deyimleri aynı satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="6db42-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="6db42-231">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-231">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="6db42-232">CSharp \_ Yeni \_ satır \_ before_catch</span><span class="sxs-lookup"><span data-stu-id="6db42-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="6db42-233">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-233">Property</span></span>|<span data-ttu-id="6db42-234">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-234">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-235">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-235">**Option name**</span></span> | <span data-ttu-id="6db42-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="6db42-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="6db42-237">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-237">**Applicable languages**</span></span> | <span data-ttu-id="6db42-238">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-238">C#</span></span> |
| <span data-ttu-id="6db42-239">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-239">**Introduced version**</span></span> | <span data-ttu-id="6db42-240">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-241">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-241">**Option values**</span></span> | <span data-ttu-id="6db42-242">`true` - `catch` Deyimlerini yeni bir satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="6db42-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="6db42-243">`false` - `catch` Deyimleri aynı satıra yerleştir.</span><span class="sxs-lookup"><span data-stu-id="6db42-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="6db42-244">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-244">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="6db42-245">CSharp \_ Yeni \_ satır \_ before_finally</span><span class="sxs-lookup"><span data-stu-id="6db42-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="6db42-246">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-246">Property</span></span>|<span data-ttu-id="6db42-247">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-247">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-248">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-248">**Option name**</span></span> | <span data-ttu-id="6db42-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="6db42-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="6db42-250">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-250">**Applicable languages**</span></span> | <span data-ttu-id="6db42-251">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-251">C#</span></span> |
| <span data-ttu-id="6db42-252">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-252">**Introduced version**</span></span> | <span data-ttu-id="6db42-253">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-254">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-254">**Option values**</span></span> | <span data-ttu-id="6db42-255">`true` - `finally` Deyimlerin, kapanış ayracından sonra yeni bir satırda olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="6db42-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="6db42-256">`false` - `finally` Deyimlerinin kapanış ayracı ile aynı satırda olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="6db42-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="6db42-257">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-257">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="6db42-258">\_ \_ \_ \_ object_initializers üyelerinizden önce \_ CSharp yeni \_ satır</span><span class="sxs-lookup"><span data-stu-id="6db42-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="6db42-259">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-259">Property</span></span>|<span data-ttu-id="6db42-260">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-260">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-261">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-261">**Option name**</span></span> | <span data-ttu-id="6db42-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="6db42-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="6db42-263">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-263">**Applicable languages**</span></span> | <span data-ttu-id="6db42-264">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-264">C#</span></span> |
| <span data-ttu-id="6db42-265">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-265">**Introduced version**</span></span> | <span data-ttu-id="6db42-266">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-267">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-267">**Option values**</span></span> | <span data-ttu-id="6db42-268">`true` -Nesne başlatıcılarının üyelerinin ayrı satırlarda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="6db42-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="6db42-269">`false` -Nesne başlatıcılarının üyelerinin aynı satırda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="6db42-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="6db42-270">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-270">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="6db42-271">\_ \_ \_ \_ anonymous_types üyelerinizden önce \_ CSharp yeni \_ satır</span><span class="sxs-lookup"><span data-stu-id="6db42-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="6db42-272">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-272">Property</span></span>|<span data-ttu-id="6db42-273">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-273">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-274">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-274">**Option name**</span></span> | <span data-ttu-id="6db42-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="6db42-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="6db42-276">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-276">**Applicable languages**</span></span> | <span data-ttu-id="6db42-277">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-277">C#</span></span> |
| <span data-ttu-id="6db42-278">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-278">**Introduced version**</span></span> | <span data-ttu-id="6db42-279">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-280">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-280">**Option values**</span></span> | <span data-ttu-id="6db42-281">`true` -Anonim türlerin üyelerinin ayrı satırlarda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="6db42-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="6db42-282">`false` -Anonim türlerin üyelerinin aynı satırda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="6db42-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="6db42-283">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-283">Code examples:</span></span>

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

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="6db42-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="6db42-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="6db42-285">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-285">Property</span></span>|<span data-ttu-id="6db42-286">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-286">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-287">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-287">**Option name**</span></span> | <span data-ttu-id="6db42-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="6db42-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="6db42-289">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-289">**Applicable languages**</span></span> | <span data-ttu-id="6db42-290">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-290">C#</span></span> |
| <span data-ttu-id="6db42-291">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-291">**Introduced version**</span></span> | <span data-ttu-id="6db42-292">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-293">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-293">**Option values**</span></span> | <span data-ttu-id="6db42-294">`true` -Sorgu ifadesi yan tümcelerinin öğelerinin ayrı satırlarda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="6db42-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="6db42-295">`false` -Sorgu ifadesi yan tümcelerinin öğelerin aynı satırda olmasını gerektir</span><span class="sxs-lookup"><span data-stu-id="6db42-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="6db42-296">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="6db42-297">Girintileme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-297">Indentation options</span></span>

<span data-ttu-id="6db42-298">Bu biçimlendirme kuralları kodu biçimlendirmek için girintileme kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6db42-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="6db42-299">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6db42-299">Example *.editorconfig* file:</span></span>

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

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="6db42-300">CSharp \_ girintileme \_ case_contents</span><span class="sxs-lookup"><span data-stu-id="6db42-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="6db42-301">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-301">Property</span></span>|<span data-ttu-id="6db42-302">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-302">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-303">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-303">**Option name**</span></span> | <span data-ttu-id="6db42-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="6db42-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="6db42-305">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-305">**Applicable languages**</span></span> | <span data-ttu-id="6db42-306">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-306">C#</span></span> |
| <span data-ttu-id="6db42-307">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-307">**Introduced version**</span></span> | <span data-ttu-id="6db42-308">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-309">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-309">**Option values**</span></span> | <span data-ttu-id="6db42-310">`true` - `switch` Case içeriğini Girintile</span><span class="sxs-lookup"><span data-stu-id="6db42-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="6db42-311">`false` - `switch` Servis talebi içeriklerini girintileme</span><span class="sxs-lookup"><span data-stu-id="6db42-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="6db42-312">Bu kural **true** olarak ayarlandığında, ı.</span><span class="sxs-lookup"><span data-stu-id="6db42-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="6db42-313">Bu kural **false**, d olarak ayarlandığında.</span><span class="sxs-lookup"><span data-stu-id="6db42-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="6db42-314">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-314">Code examples:</span></span>

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

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="6db42-315">CSharp \_ girintileme \_ switch_labels</span><span class="sxs-lookup"><span data-stu-id="6db42-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="6db42-316">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-316">Property</span></span>|<span data-ttu-id="6db42-317">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-317">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-318">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-318">**Option name**</span></span> | <span data-ttu-id="6db42-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="6db42-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="6db42-320">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-320">**Applicable languages**</span></span> | <span data-ttu-id="6db42-321">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-321">C#</span></span> |
| <span data-ttu-id="6db42-322">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-322">**Introduced version**</span></span> | <span data-ttu-id="6db42-323">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-324">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-324">**Option values**</span></span> | <span data-ttu-id="6db42-325">`true` - `switch` Etiketleri Girintile</span><span class="sxs-lookup"><span data-stu-id="6db42-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="6db42-326">`false` - `switch` Etiketleri girintileme</span><span class="sxs-lookup"><span data-stu-id="6db42-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="6db42-327">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-327">Code examples:</span></span>

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

#### <a name="csharp_indent_labels"></a><span data-ttu-id="6db42-328">CSharp \_ indent_labels</span><span class="sxs-lookup"><span data-stu-id="6db42-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="6db42-329">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-329">Property</span></span>|<span data-ttu-id="6db42-330">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-330">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-331">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-331">**Option name**</span></span> | <span data-ttu-id="6db42-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="6db42-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="6db42-333">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-333">**Applicable languages**</span></span> | <span data-ttu-id="6db42-334">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-334">C#</span></span> |
| <span data-ttu-id="6db42-335">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-335">**Introduced version**</span></span> | <span data-ttu-id="6db42-336">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-337">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-337">**Option values**</span></span> | <span data-ttu-id="6db42-338">`flush_left` -Etiketler en soldaki sütuna yerleştirilir</span><span class="sxs-lookup"><span data-stu-id="6db42-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="6db42-339">`one_less_than_current` -Etiketler geçerli bağlama göre daha az bir girintide yerleştirilir</span><span class="sxs-lookup"><span data-stu-id="6db42-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="6db42-340">`no_change` -Etiketler, geçerli bağlamla aynı girintide yer alır</span><span class="sxs-lookup"><span data-stu-id="6db42-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="6db42-341">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-341">Code examples:</span></span>

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

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="6db42-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="6db42-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="6db42-343">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-343">Property</span></span>|<span data-ttu-id="6db42-344">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-344">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-345">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-345">**Option name**</span></span> | <span data-ttu-id="6db42-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="6db42-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="6db42-347">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-347">**Applicable languages**</span></span> | <span data-ttu-id="6db42-348">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-348">C#</span></span> |
| <span data-ttu-id="6db42-349">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="6db42-350">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-350">Code examples:</span></span>

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

#### <a name="csharp_indent_braces"></a><span data-ttu-id="6db42-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="6db42-351">csharp_indent_braces</span></span>

|<span data-ttu-id="6db42-352">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-352">Property</span></span>|<span data-ttu-id="6db42-353">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-353">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-354">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-354">**Option name**</span></span> | <span data-ttu-id="6db42-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="6db42-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="6db42-356">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-356">**Applicable languages**</span></span> | <span data-ttu-id="6db42-357">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-357">C#</span></span> |
| <span data-ttu-id="6db42-358">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="6db42-359">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-359">Code examples:</span></span>

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

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="6db42-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="6db42-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="6db42-361">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-361">Property</span></span>|<span data-ttu-id="6db42-362">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-362">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-363">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-363">**Option name**</span></span> | <span data-ttu-id="6db42-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="6db42-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="6db42-365">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-365">**Applicable languages**</span></span> | <span data-ttu-id="6db42-366">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-366">C#</span></span> |
| <span data-ttu-id="6db42-367">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="6db42-368">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-368">Code examples:</span></span>

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

### <a name="spacing-options"></a><span data-ttu-id="6db42-369">Aralık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-369">Spacing options</span></span>

<span data-ttu-id="6db42-370">Bu biçimlendirme kuralları kodu biçimlendirmek için boşluk karakterlerinin kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6db42-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="6db42-371">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6db42-371">Example *.editorconfig* file:</span></span>

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

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="6db42-372">CSharp \_ space \_ after_cast</span><span class="sxs-lookup"><span data-stu-id="6db42-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="6db42-373">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-373">Property</span></span>|<span data-ttu-id="6db42-374">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-374">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-375">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-375">**Option name**</span></span> | <span data-ttu-id="6db42-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="6db42-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="6db42-377">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-377">**Applicable languages**</span></span> | <span data-ttu-id="6db42-378">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-378">C#</span></span> |
| <span data-ttu-id="6db42-379">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-379">**Introduced version**</span></span> | <span data-ttu-id="6db42-380">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-381">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-381">**Option values**</span></span> | <span data-ttu-id="6db42-382">`true` -Bir atama ve değer arasına bir boşluk karakteri koyun</span><span class="sxs-lookup"><span data-stu-id="6db42-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="6db42-383">`false` -Cast ve değer arasındaki boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="6db42-384">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="6db42-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="6db42-386">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-386">Property</span></span>|<span data-ttu-id="6db42-387">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-387">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-388">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-388">**Option name**</span></span> | <span data-ttu-id="6db42-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="6db42-390">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-390">**Applicable languages**</span></span> | <span data-ttu-id="6db42-391">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-391">C#</span></span> |
| <span data-ttu-id="6db42-392">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-392">**Introduced version**</span></span> | <span data-ttu-id="6db42-393">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-394">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-394">**Option values**</span></span> | <span data-ttu-id="6db42-395">`true`-Döngü gibi bir denetim akışı deyimindeki anahtar sözcükten sonra bir boşluk karakteri yerleştir `for`</span><span class="sxs-lookup"><span data-stu-id="6db42-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="6db42-396">`false`-Döngü gibi bir denetim akışı deyimindeki anahtar sözcükten sonra boşluk Kaldır `for`</span><span class="sxs-lookup"><span data-stu-id="6db42-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="6db42-397">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="6db42-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="6db42-399">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-399">Property</span></span>|<span data-ttu-id="6db42-400">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-400">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-401">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-401">**Option name**</span></span> | <span data-ttu-id="6db42-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="6db42-403">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-403">**Applicable languages**</span></span> | <span data-ttu-id="6db42-404">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-404">C#</span></span> |
| <span data-ttu-id="6db42-405">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-405">**Introduced version**</span></span> | <span data-ttu-id="6db42-406">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-407">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-407">**Option values**</span></span> | <span data-ttu-id="6db42-408">`control_flow_statements` -Denetim akışı deyimlerinin parantezleri arasına boşluk yerleştir</span><span class="sxs-lookup"><span data-stu-id="6db42-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="6db42-409">`expressions` -İfadelerin parantezleri arasına boşluk yerleştir</span><span class="sxs-lookup"><span data-stu-id="6db42-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="6db42-410">`type_casts` -Tür atamalerdeki parantezler arasında boşluk yerleştir</span><span class="sxs-lookup"><span data-stu-id="6db42-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="6db42-411">Bu kuralı atlarsanız veya,, veya dışında bir değer kullanırsanız `control_flow_statements` , `expressions` `type_casts` ayar uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="6db42-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="6db42-412">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="6db42-413">\_ \_ \_ inheritance_clause iki noktadan önce \_ CSharp \_ Space</span><span class="sxs-lookup"><span data-stu-id="6db42-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="6db42-414">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-414">Property</span></span>|<span data-ttu-id="6db42-415">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-415">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-416">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-416">**Option name**</span></span> | <span data-ttu-id="6db42-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="6db42-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="6db42-418">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-418">**Applicable languages**</span></span> | <span data-ttu-id="6db42-419">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-419">C#</span></span> |
| <span data-ttu-id="6db42-420">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-420">**Introduced version**</span></span> | <span data-ttu-id="6db42-421">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="6db42-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="6db42-422">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-422">**Option values**</span></span> | <span data-ttu-id="6db42-423">`true` -Bir tür bildiriminde temeller veya arabirimler için iki noktadan önce bir boşluk karakteri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="6db42-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="6db42-424">`false` -Tür bildiriminde temeller veya arabirimler için iki noktadan önce boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="6db42-425">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-425">Code examples:</span></span>

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="6db42-426">\_ \_ \_ inheritance_clause iki noktadan sonra \_ CSharp \_ Space</span><span class="sxs-lookup"><span data-stu-id="6db42-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="6db42-427">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-427">Property</span></span>|<span data-ttu-id="6db42-428">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-428">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-429">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-429">**Option name**</span></span> | <span data-ttu-id="6db42-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="6db42-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="6db42-431">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-431">**Applicable languages**</span></span> | <span data-ttu-id="6db42-432">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-432">C#</span></span> |
| <span data-ttu-id="6db42-433">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-433">**Introduced version**</span></span> | <span data-ttu-id="6db42-434">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="6db42-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="6db42-435">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-435">**Option values**</span></span> | <span data-ttu-id="6db42-436">`true` -Bir tür bildiriminde tabanların veya arabirimlerin iki noktadan sonra bir boşluk karakteri yerleştir</span><span class="sxs-lookup"><span data-stu-id="6db42-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="6db42-437">`false` -Bir tür bildiriminde temeller veya arabirimler için iki noktadan sonra boşluk kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="6db42-438">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-438">Code examples:</span></span>

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

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="6db42-439">\_ \_ binary_operators etrafında CSharp \_ alanı</span><span class="sxs-lookup"><span data-stu-id="6db42-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="6db42-440">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-440">Property</span></span>|<span data-ttu-id="6db42-441">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-441">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-442">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-442">**Option name**</span></span> | <span data-ttu-id="6db42-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6db42-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="6db42-444">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-444">**Applicable languages**</span></span> | <span data-ttu-id="6db42-445">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-445">C#</span></span> |
| <span data-ttu-id="6db42-446">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-446">**Introduced version**</span></span> | <span data-ttu-id="6db42-447">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="6db42-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="6db42-448">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-448">**Option values**</span></span> | <span data-ttu-id="6db42-449">`before_and_after` -İkili işleçten önce ve sonra boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="6db42-450">`none` -İkili işleçten önce ve sonra boşlukları kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="6db42-451">`ignore` -İkili operatörlerin çevresindeki boşlukları yoksay</span><span class="sxs-lookup"><span data-stu-id="6db42-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="6db42-452">Bu kuralı atlarsanız veya,, veya dışında bir değer kullanırsanız, `before_and_after` `none` `ignore` ayar uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="6db42-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="6db42-453">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="6db42-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="6db42-455">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-455">Property</span></span>|<span data-ttu-id="6db42-456">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-456">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-457">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-457">**Option name**</span></span> | <span data-ttu-id="6db42-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="6db42-459">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-459">**Applicable languages**</span></span> | <span data-ttu-id="6db42-460">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-460">C#</span></span> |
| <span data-ttu-id="6db42-461">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-461">**Introduced version**</span></span> | <span data-ttu-id="6db42-462">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-463">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-463">**Option values**</span></span> | <span data-ttu-id="6db42-464">`true` -Açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce bir boşluk karakteri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="6db42-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="6db42-465">`false` -Boşluk karakterlerini açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce kaldırın</span><span class="sxs-lookup"><span data-stu-id="6db42-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="6db42-466">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="6db42-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="6db42-468">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-468">Property</span></span>|<span data-ttu-id="6db42-469">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-469">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-470">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-470">**Option name**</span></span> | <span data-ttu-id="6db42-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="6db42-472">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-472">**Applicable languages**</span></span> | <span data-ttu-id="6db42-473">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-473">C#</span></span> |
| <span data-ttu-id="6db42-474">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-474">**Introduced version**</span></span> | <span data-ttu-id="6db42-475">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="6db42-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="6db42-476">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-476">**Option values**</span></span> | <span data-ttu-id="6db42-477">`true` -Yöntem bildirimi için boş parametre listesi ayraçları içine boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="6db42-478">`false` -Yöntem bildirimi için boş parametre listesi ayraçları içindeki alanı kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="6db42-479">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-479">Code examples:</span></span>

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

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="6db42-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="6db42-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="6db42-481">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-481">Property</span></span>|<span data-ttu-id="6db42-482">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-482">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-483">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-483">**Option name**</span></span> | <span data-ttu-id="6db42-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="6db42-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="6db42-485">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-485">**Applicable languages**</span></span> | <span data-ttu-id="6db42-486">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-486">C#</span></span> |
| <span data-ttu-id="6db42-487">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-487">**Option values**</span></span> | <span data-ttu-id="6db42-488">`true` -Yöntem bildiriminde Yöntem adı ve açma ayracı arasına bir boşluk karakteri koyun</span><span class="sxs-lookup"><span data-stu-id="6db42-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="6db42-489">`false` -Yöntem bildiriminde Yöntem adı ve açma ayracı arasındaki boşluk karakterlerini kaldırın</span><span class="sxs-lookup"><span data-stu-id="6db42-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="6db42-490">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="6db42-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="6db42-492">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-492">Property</span></span>|<span data-ttu-id="6db42-493">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-493">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-494">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-494">**Option name**</span></span> | <span data-ttu-id="6db42-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="6db42-496">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-496">**Applicable languages**</span></span> | <span data-ttu-id="6db42-497">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-497">C#</span></span> |
| <span data-ttu-id="6db42-498">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-498">**Introduced version**</span></span> | <span data-ttu-id="6db42-499">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-500">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-500">**Option values**</span></span> | <span data-ttu-id="6db42-501">`true` -Açma parantezinden sonra ve bir yöntem çağrısının kapatma parantezinden önce bir boşluk karakteri yerleştirin</span><span class="sxs-lookup"><span data-stu-id="6db42-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="6db42-502">`false` -Açma parantezinden sonra ve bir yöntem çağrısının kapanış parantezinden önce boşluk karakterlerini kaldırın</span><span class="sxs-lookup"><span data-stu-id="6db42-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="6db42-503">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="6db42-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="6db42-505">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-505">Property</span></span>|<span data-ttu-id="6db42-506">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-506">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-507">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-507">**Option name**</span></span> | <span data-ttu-id="6db42-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="6db42-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="6db42-509">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-509">**Applicable languages**</span></span> | <span data-ttu-id="6db42-510">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-510">C#</span></span> |
| <span data-ttu-id="6db42-511">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-511">**Introduced version**</span></span> | <span data-ttu-id="6db42-512">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="6db42-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="6db42-513">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-513">**Option values**</span></span> | <span data-ttu-id="6db42-514">`true` -Boş bağımsız değişken listesi ayraçları içine boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="6db42-515">`false` -Boş bağımsız değişken listesi ayraçları içindeki alanı kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="6db42-516">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-516">Code examples:</span></span>

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

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="6db42-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="6db42-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="6db42-518">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-518">Property</span></span>|<span data-ttu-id="6db42-519">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-519">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-520">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-520">**Option name**</span></span> | <span data-ttu-id="6db42-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="6db42-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="6db42-522">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-522">**Applicable languages**</span></span> | <span data-ttu-id="6db42-523">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-523">C#</span></span> |
| <span data-ttu-id="6db42-524">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-524">**Introduced version**</span></span> | <span data-ttu-id="6db42-525">Visual Studio 2017 sürüm 15.7 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="6db42-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="6db42-526">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-526">**Option values**</span></span> | <span data-ttu-id="6db42-527">`true` -Yöntem çağrısı adı ve açma ayracı arasına boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="6db42-528">`false` -Yöntem çağrı adı ve açılış ayracı arasındaki boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="6db42-529">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-529">Code examples:</span></span>

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

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="6db42-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="6db42-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="6db42-531">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-531">Property</span></span>|<span data-ttu-id="6db42-532">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-532">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-533">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-533">**Option name**</span></span> | <span data-ttu-id="6db42-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="6db42-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="6db42-535">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-535">**Applicable languages**</span></span> | <span data-ttu-id="6db42-536">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-536">C#</span></span> |
| <span data-ttu-id="6db42-537">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-537">**Option values**</span></span> | <span data-ttu-id="6db42-538">`true` -Virgülden sonra boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="6db42-539">`false` -Virgülden sonra boşluk kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="6db42-540">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="6db42-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="6db42-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="6db42-542">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-542">Property</span></span>|<span data-ttu-id="6db42-543">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-543">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-544">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-544">**Option name**</span></span> | <span data-ttu-id="6db42-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="6db42-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="6db42-546">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-546">**Applicable languages**</span></span> | <span data-ttu-id="6db42-547">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-547">C#</span></span> |
| <span data-ttu-id="6db42-548">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-548">**Option values**</span></span> | <span data-ttu-id="6db42-549">`true` -Virgülden önce boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="6db42-550">`false` -Bir virgülden önce boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="6db42-551">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="6db42-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="6db42-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="6db42-553">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-553">Property</span></span>|<span data-ttu-id="6db42-554">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-554">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-555">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-555">**Option name**</span></span> | <span data-ttu-id="6db42-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="6db42-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="6db42-557">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-557">**Applicable languages**</span></span> | <span data-ttu-id="6db42-558">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-558">C#</span></span> |
| <span data-ttu-id="6db42-559">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-559">**Option values**</span></span> | <span data-ttu-id="6db42-560">`true` -Noktadan sonra boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="6db42-561">`false` -Noktadan sonra boşluk kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="6db42-562">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="6db42-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="6db42-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="6db42-564">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-564">Property</span></span>|<span data-ttu-id="6db42-565">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-565">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-566">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-566">**Option name**</span></span> | <span data-ttu-id="6db42-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="6db42-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="6db42-568">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-568">**Applicable languages**</span></span> | <span data-ttu-id="6db42-569">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-569">C#</span></span> |
| <span data-ttu-id="6db42-570">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-570">**Option values**</span></span> | <span data-ttu-id="6db42-571">`true` -Noktadan önce boşluk Ekle</span><span class="sxs-lookup"><span data-stu-id="6db42-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="6db42-572">`false` -Noktadan önce boşluğu kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="6db42-573">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="6db42-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="6db42-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="6db42-575">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-575">Property</span></span>|<span data-ttu-id="6db42-576">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-576">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-577">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-577">**Option name**</span></span> | <span data-ttu-id="6db42-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="6db42-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="6db42-579">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-579">**Applicable languages**</span></span> | <span data-ttu-id="6db42-580">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-580">C#</span></span> |
| <span data-ttu-id="6db42-581">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-581">**Option values**</span></span> | <span data-ttu-id="6db42-582">`true`-Bir ifadede her noktalı virgülden sonra boşluk Ekle `for`</span><span class="sxs-lookup"><span data-stu-id="6db42-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="6db42-583">`false`-Bir bildirimde her noktalı virgülden sonra boşluk Kaldır `for`</span><span class="sxs-lookup"><span data-stu-id="6db42-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="6db42-584">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="6db42-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="6db42-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="6db42-586">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-586">Property</span></span>|<span data-ttu-id="6db42-587">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-587">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-588">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-588">**Option name**</span></span> | <span data-ttu-id="6db42-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="6db42-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="6db42-590">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-590">**Applicable languages**</span></span> | <span data-ttu-id="6db42-591">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-591">C#</span></span> |
| <span data-ttu-id="6db42-592">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-592">**Option values**</span></span> | <span data-ttu-id="6db42-593">`true`-Bir bildirimde her noktalı virgülden önce boşluk Ekle `for`</span><span class="sxs-lookup"><span data-stu-id="6db42-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="6db42-594">`false`-Bir bildirimde her noktalı virgülden önce boşluk Kaldır `for`</span><span class="sxs-lookup"><span data-stu-id="6db42-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="6db42-595">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="6db42-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="6db42-597">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-597">Property</span></span>|<span data-ttu-id="6db42-598">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-598">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-599">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-599">**Option name**</span></span> | <span data-ttu-id="6db42-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="6db42-601">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-601">**Applicable languages**</span></span> | <span data-ttu-id="6db42-602">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-602">C#</span></span> |
| <span data-ttu-id="6db42-603">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-603">**Option values**</span></span> | <span data-ttu-id="6db42-604">`ignore` -Bildirim deyimlerine fazladan boşluk karakterleri kaldırmayın</span><span class="sxs-lookup"><span data-stu-id="6db42-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="6db42-605">`false` -Bildirim deyimlerine ek boşluk karakterlerini kaldır</span><span class="sxs-lookup"><span data-stu-id="6db42-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="6db42-606">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="6db42-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="6db42-608">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-608">Property</span></span>|<span data-ttu-id="6db42-609">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-609">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-610">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-610">**Option name**</span></span> | <span data-ttu-id="6db42-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="6db42-612">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-612">**Applicable languages**</span></span> | <span data-ttu-id="6db42-613">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-613">C#</span></span> |
| <span data-ttu-id="6db42-614">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-614">**Option values**</span></span> | <span data-ttu-id="6db42-615">`true` -Açılış köşeli ayracından önce boşluk Ekle `[`</span><span class="sxs-lookup"><span data-stu-id="6db42-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="6db42-616">`false` -Köşeli ayraçları açmadan önce boşluğu kaldır `[`</span><span class="sxs-lookup"><span data-stu-id="6db42-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="6db42-617">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="6db42-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="6db42-619">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-619">Property</span></span>|<span data-ttu-id="6db42-620">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-620">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-621">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-621">**Option name**</span></span> | <span data-ttu-id="6db42-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="6db42-623">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-623">**Applicable languages**</span></span> | <span data-ttu-id="6db42-624">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-624">C#</span></span> |
| <span data-ttu-id="6db42-625">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-625">**Option values**</span></span> | <span data-ttu-id="6db42-626">`true` -Boş köşeli ayraç arasına boşluk Ekle `[ ]`</span><span class="sxs-lookup"><span data-stu-id="6db42-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="6db42-627">`false` -Boş köşeli ayraçlar arasındaki boşluğu kaldır `[]`</span><span class="sxs-lookup"><span data-stu-id="6db42-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="6db42-628">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="6db42-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="6db42-630">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-630">Property</span></span>|<span data-ttu-id="6db42-631">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-631">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-632">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-632">**Option name**</span></span> | <span data-ttu-id="6db42-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="6db42-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="6db42-634">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-634">**Applicable languages**</span></span> | <span data-ttu-id="6db42-635">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-635">C#</span></span> |
| <span data-ttu-id="6db42-636">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-636">**Option values**</span></span> | <span data-ttu-id="6db42-637">`true` -Boş olmayan köşeli Parantezde boşluk karakterleri Ekle `[ 0 ]`</span><span class="sxs-lookup"><span data-stu-id="6db42-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="6db42-638">`false` -Boş olmayan köşeli ayraçdaki boşluk karakterlerini kaldır `[0]`</span><span class="sxs-lookup"><span data-stu-id="6db42-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="6db42-639">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="6db42-640">Sarlama seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6db42-640">Wrap options</span></span>

<span data-ttu-id="6db42-641">Bu biçimlendirme kuralları, deyimler ve kod blokları için ayrı satırlara karşı tek satırların kullanımını önemli olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="6db42-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="6db42-642">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6db42-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="6db42-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="6db42-644">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-644">Property</span></span>|<span data-ttu-id="6db42-645">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-645">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-646">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-646">**Option name**</span></span> | <span data-ttu-id="6db42-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="6db42-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="6db42-648">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-648">**Applicable languages**</span></span> | <span data-ttu-id="6db42-649">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-649">C#</span></span> |
| <span data-ttu-id="6db42-650">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-650">**Introduced version**</span></span> | <span data-ttu-id="6db42-651">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-652">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-652">**Option values**</span></span> | <span data-ttu-id="6db42-653">`true` -Deyimleri ve üye bildirimlerini aynı satırda bırak</span><span class="sxs-lookup"><span data-stu-id="6db42-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="6db42-654">`false` -Deyimleri ve üye bildirimlerini farklı satırlarda bırak</span><span class="sxs-lookup"><span data-stu-id="6db42-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="6db42-655">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="6db42-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="6db42-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="6db42-657">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-657">Property</span></span>|<span data-ttu-id="6db42-658">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-658">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-659">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-659">**Option name**</span></span> | <span data-ttu-id="6db42-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="6db42-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="6db42-661">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-661">**Applicable languages**</span></span> | <span data-ttu-id="6db42-662">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-662">C#</span></span> |
| <span data-ttu-id="6db42-663">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-663">**Introduced version**</span></span> | <span data-ttu-id="6db42-664">Visual Studio 2017 sürüm 15.3</span><span class="sxs-lookup"><span data-stu-id="6db42-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="6db42-665">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-665">**Option values**</span></span> | <span data-ttu-id="6db42-666">`true` -Kod bloğunu tek satırda bırak</span><span class="sxs-lookup"><span data-stu-id="6db42-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="6db42-667">`false` -Kod bloğunu ayrı satırlarda bırak</span><span class="sxs-lookup"><span data-stu-id="6db42-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="6db42-668">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="6db42-669">Yönerge seçeneklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6db42-669">Using directive options</span></span>

<span data-ttu-id="6db42-670">Bu biçimlendirme kuralı, bir ad alanı dışında, içine yerleştirilmiş yönergelerin kullanımı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="6db42-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="6db42-671">Örnek *. editorconfig* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6db42-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="6db42-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="6db42-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="6db42-673">Özellik</span><span class="sxs-lookup"><span data-stu-id="6db42-673">Property</span></span>|<span data-ttu-id="6db42-674">Değer</span><span class="sxs-lookup"><span data-stu-id="6db42-674">Value</span></span>|
|-|-|
| <span data-ttu-id="6db42-675">**Seçenek adı**</span><span class="sxs-lookup"><span data-stu-id="6db42-675">**Option name**</span></span> | <span data-ttu-id="6db42-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="6db42-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="6db42-677">**Uygun diller**</span><span class="sxs-lookup"><span data-stu-id="6db42-677">**Applicable languages**</span></span> | <span data-ttu-id="6db42-678">C#</span><span class="sxs-lookup"><span data-stu-id="6db42-678">C#</span></span> |
| <span data-ttu-id="6db42-679">**Tanıtılan sürüm**</span><span class="sxs-lookup"><span data-stu-id="6db42-679">**Introduced version**</span></span> | <span data-ttu-id="6db42-680"> Visual Studio 2019 sürüm 16.1</span><span class="sxs-lookup"><span data-stu-id="6db42-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="6db42-681">**Seçenek değerleri**</span><span class="sxs-lookup"><span data-stu-id="6db42-681">**Option values**</span></span> | <span data-ttu-id="6db42-682">`outside_namespace` -Ad alanı dışındaki yönergeleri kullanmayı bırak</span><span class="sxs-lookup"><span data-stu-id="6db42-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="6db42-683">`inside_namespace` -Ad alanı içinde yönergeleri kullanmayı bırak</span><span class="sxs-lookup"><span data-stu-id="6db42-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="6db42-684">Kod örnekleri:</span><span class="sxs-lookup"><span data-stu-id="6db42-684">Code examples:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6db42-685">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6db42-685">See also</span></span>

- [<span data-ttu-id="6db42-686">Dil kuralları</span><span class="sxs-lookup"><span data-stu-id="6db42-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="6db42-687">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="6db42-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="6db42-688">.NET kod stili kuralları başvurusu</span><span class="sxs-lookup"><span data-stu-id="6db42-688">.NET code style rules reference</span></span>](index.md)
