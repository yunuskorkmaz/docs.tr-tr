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
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957981"
---
# <a name="language-rules"></a>Dil kuralları

Kod stili dil kuralları, .NET programlama dillerinin çeşitli yapılarının, örneğin değiştiricilerin ve parantezlerin nasıl kullanıldığını etkiler. Kurallar aşağıdaki kategorilere ayrılır:

- [.Net stil kuralları](#net-style-rules): hem C# hem de Visual Basic için uygulanan kurallar. Bu kuralların EditorConfig seçenek adları `dotnet_style_` ön Ekle başlar.
- [C# stil kuralları](#c-style-rules): yalnızca c# diline özgü kurallardır. Bu kuralların EditorConfig seçenek adları `csharp_style_` ön Ekle başlar.
- [Visual Basic stil kuralları](#visual-basic-style-rules): yalnızca Visual Bsic diline özgü kurallardır. Bu kuralların EditorConfig seçenek adları `visual_basic_style_` ön Ekle başlar.

## <a name="option-format"></a>Seçenek biçimi

Dil kuralları seçenekleri aşağıdaki biçimde bir EditorConfig dosyasında belirtilebilir:

`option_name = value` (Visual Studio 2019 sürüm 16,9 Preview 2 ve üzeri)

veya

`option_name = value:severity`

- **Değer**

  Her dil kuralı için, stilin ne zaman tercih edilmesi gerektiğini tanımlayan bir değer belirtirsiniz. Birçok kural bir değeri kabul eder `true` (Bu stili tercih et) veya `false` (Bu stili tercih etme). Diğer kurallar veya gibi değerleri kabul `when_on_single_line` eder `never` .

- **Önem derecesi** (Visual Studio 2019 sürüm 16,9 Preview 2 ve sonraki sürümler için isteğe bağlı)

  Kuralın ikinci bölümü, kuralın [önem derecesini](../configuration-options.md#severity-level) belirtir. Bu şekilde belirtildiğinde önem derecesi ayarı yalnızca Visual Studio gibi geliştirme IDEs 'in içinde olur. Derleme sırasında dikkate *verilmez* .

  Derleme zamanında kod stili kuralları zorlamak için, bunun yerine çözümleyiciler için kural KIMLIĞI tabanlı önem derecesi yapılandırma sözdizimini kullanarak önem derecesini ayarlayın. Sözdizimi, `dotnet_diagnostic.<rule ID>.severity = <severity>` Örneğin, biçimini alır `dotnet_diagnostic.IDE0040.severity = silent` . Daha fazla bilgi için bkz. [önem düzeyi](../configuration-options.md#severity-level).

> [!TIP]
>
> Visual Studio 2019 sürüm 16,3 ' den başlayarak, bir stil ihlali oluştuktan sonra [hızlı eylemler](/visualstudio/ide/quick-actions) ampul menüsünden kod stili kurallarını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da kod stillerini otomatik olarak yapılandırma](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).

## <a name="net-style-rules"></a>.NET stil kuralları

Bu bölümdeki stil kuralları hem C# hem de Visual Basic için geçerlidir.

- [' this. ' ve ' me. ' niteleyicileri](ide0003-ide0009.md)
  - [dotnet_style_qualification_for_field](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [dotnet_style_qualification_for_property](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [dotnet_style_qualification_for_method](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [dotnet_style_qualification_for_event](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [Tür başvuruları için çerçeve türü adları yerine dil anahtar sözcükleri](ide0049.md)
  - [dotnet_style_predefined_type_for_locals_parameters_members](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [dotnet_style_predefined_type_for_member_access](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [Değiştirici tercihleri](modifier-preferences.md#net-modifier-preferences)
  - [dotnet_style_require_accessibility_modifiers](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [csharp_preferred_modifier_order](ide0036.md#csharp_preferred_modifier_order)
  - [visual_basic_preferred_modifier_order](ide0036.md#visual_basic_preferred_modifier_order)
  - [dotnet_style_readonly_field](ide0044.md#dotnet_style_readonly_field)
- [Parantez tercihleri](ide0047-ide0048.md)
  - [dotnet_style_parentheses_in_arithmetic_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [dotnet_style_parentheses_in_relational_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [dotnet_style_parentheses_in_other_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [dotnet_style_parentheses_in_other_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [İfade düzeyinde tercihler](expression-level-preferences.md#net-expression-level-preferences)
  - [dotnet_style_object_initializer](ide0017.md#dotnet_style_object_initializer)
  - [dotnet_style_collection_initializer](ide0028.md#dotnet_style_collection_initializer)
  - [dotnet_style_explicit_tuple_names](ide0033.md#dotnet_style_explicit_tuple_names)
  - [dotnet_style_prefer_inferred_tuple_names](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [dotnet_style_prefer_inferred_anonymous_type_member_names](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [dotnet_style_prefer_auto_properties](ide0032.md#dotnet_style_prefer_auto_properties)
  - [dotnet_style_prefer_conditional_expression_over_assignment](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [dotnet_style_prefer_conditional_expression_over_return](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [dotnet_style_prefer_compound_assignment](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [dotnet_style_prefer_simplified_interpolation](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [dotnet_style_prefer_simplified_boolean_expressions](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - [Switch ifadesine eksik durumları Ekle](ide0010.md) -bu kuralda kod stili seçeneği yok.
  - [Anonim türü kayıt tipine Dönüştür](ide0050.md) -bu kuralda kod stili seçeneği yoktur.
  - [' System. HashCode. Birleştir ' kullanın](ide0070.md) -bu kuralda kod stili seçeneği yoktur.
  - [' Typeof ' öğesini ' NameOf ' öğesine Dönüştür](ide0082.md) -bu kuralda kod stili seçeneği yoktur.
- [Null denetleme tercihleri](null-checking-preferences.md#net-null-checking-preferences)
  - [dotnet_style_coalesce_expression](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [dotnet_style_null_propagation](ide0031.md#dotnet_style_null_propagation)
  - [dotnet_style_prefer_is_null_check_over_reference_equality_method](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [Dosya üst bilgisi tercihleri](ide0073.md)
  - [file_header_template](ide0073.md#file_header_template)

## <a name="c-style-rules"></a>C# stil kuralları

Bu bölümdeki stil kuralları yalnızca C# dili için geçerlidir.

- [' var ' tercihleri](ide0007-ide0008.md)
  - [csharp_style_var_for_built_in_types](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [csharp_style_var_when_type_is_apparent](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [csharp_style_var_elsewhere](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [İfade gövdeli üyeler](expression-bodied-members.md)
  - [csharp_style_expression_bodied_methods](ide0022.md#csharp_style_expression_bodied_methods)
  - [csharp_style_expression_bodied_constructors](ide0021.md#csharp_style_expression_bodied_constructors)
  - [csharp_style_expression_bodied_operators](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [csharp_style_expression_bodied_properties](ide0025.md#csharp_style_expression_bodied_properties)
  - [csharp_style_expression_bodied_indexers](ide0026.md#csharp_style_expression_bodied_indexers)
  - [csharp_style_expression_bodied_accessors](ide0027.md#csharp_style_expression_bodied_accessors)
  - [csharp_style_expression_bodied_lambdas](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [csharp_style_expression_bodied_local_functions](ide0061.md#csharp_style_expression_bodied_local_functions)
- [Desen eşleştirme tercihleri](pattern-matching-preferences.md)
  - [csharp_style_pattern_matching_over_is_with_cast_check](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [csharp_style_pattern_matching_over_as_with_null_check](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [csharp_style_prefer_switch_expression](ide0066.md#csharp_style_prefer_switch_expression)
  - [csharp_style_prefer_pattern_matching](ide0078.md#csharp_style_prefer_pattern_matching)
  - [csharp_style_prefer_not_pattern](ide0083.md#csharp_style_prefer_not_pattern)
- [İfade düzeyinde tercihler](expression-level-preferences.md#c-expression-level-preferences)
  - [csharp_style_inlined_variable_declaration](ide0018.md#csharp_style_inlined_variable_declaration)
  - [csharp_prefer_simple_default_expression](ide0034.md#csharp_prefer_simple_default_expression)
  - [csharp_style_pattern_local_over_anonymous_function](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [csharp_style_deconstructed_variable_declaration](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [csharp_style_prefer_index_operator](ide0056.md#csharp_style_prefer_index_operator)
  - [csharp_style_prefer_range_operator](ide0057.md#csharp_style_prefer_range_operator)
  - [csharp_style_implicit_object_creation_when_type_is_apparent](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - [Anahtar ifadesine eksik durum ekleme](ide0072.md) -bu kuralda kod stili seçeneği yok.
- ["Null" Denetim tercihleri](null-checking-preferences.md#c-null-checking-preferences)
  - [csharp_style_throw_expression](ide0016.md#csharp_style_throw_expression)
  - [csharp_style_conditional_delegate_call](ide1005.md#csharp_style_conditional_delegate_call)
- [Kod bloğu tercihleri](code-block-preferences.md)
  - [csharp_prefer_braces](ide0011.md#csharp_prefer_braces)
  - [csharp_prefer_simple_using_statement](ide0063.md#csharp_prefer_simple_using_statement)
- [' Using ' yönerge tercihleri](ide0065.md)
  - [csharp_using_directive_placement](ide0065.md#csharp_using_directive_placement)
- [Değiştirici tercihleri](modifier-preferences.md#c-modifier-preferences)
  - [csharp_prefer_static_local_function](ide0062.md#csharp_prefer_static_local_function)
  - [Struct alanlarını yazılabilir yap](ide0064.md) -bu kuralda kod stili seçeneği yoktur.

## <a name="visual-basic-style-rules"></a>Visual Basic stil kuralları

Bu bölümdeki stil kuralları yalnızca Visual Basic dil için geçerlidir.

- [Desen eşleştirme tercihleri](pattern-matching-preferences.md)
  - [visual_basic_style_prefer_isnot_expression](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a>Ayrıca bkz.

- [Gereksiz kod kuralları](unnecessary-code-rules.md)
- [Biçimlendirme kuralları](formatting-rules.md)
- [Adlandırma kuralları](naming-rules.md)
- [.NET kod stili kuralları başvurusu](index.md)
