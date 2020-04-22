---
title: 'C# ayrılmış öznitelikler: Koşullu, Eski, ÖznitelikKullanım'
ms.date: 04/09/2020
description: Bu öznitelikler derleyici tarafından oluşturulan kodu etkilemek için derleyici tarafından yorumlanır
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021766"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>Ayrılmış öznitelikler: Koşullu Öznitelik, EskiÖzÖzöz, ÖznitelikKullanımAttribute

Bu öznitelikler, kodunuzdaki öğelere uygulanabilir. Bu elementlere anlamsal anlam katarlar. Derleyici, çıktısını değiştirmek ve kodunuzu kullanan geliştiricilerin olası hatalarını bildirmek için bu anlamsal anlamları kullanır.

## <a name="conditional-attribute"></a>`Conditional` özniteliği

Öznitelik, `Conditional` bir yöntemin yürütülmesini bir ön işleme tanımlayıcısı bağımlı hale getirir. Öznitelik, `Conditional` <xref:System.Diagnostics.ConditionalAttribute>bir diğer adıdır ve bir yönteme veya öznitelik sınıfına uygulanabilir.

Aşağıdaki örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı etmek için bir yöntem uygulanır:

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

`TRACE_ON` Tanımlayıcı tanımlanmamışsa, izleme çıktısı görüntülenmez. Etkileşimli pencerede kendiniz keşfedin.

Öznitelik `Conditional` genellikle aşağıdaki örnekte gösterildiği gibi, hata ayıklama yapılar için izleme ve günlük özelliklerini etkinleştirmek için tanımlayıcı ile `DEBUG` kullanılır, ancak sürüm yapılarda değil:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, belirtilen ön işleme sembolünün varlığı veya yokluğu, çağrının dahil edilip edilmeyeceğini veya atlanıp atlanmayacağını belirler. Sembol tanımlanırsa, çağrı dahil edilir; aksi takdirde, arama atlanır. Koşullu yöntem, bir sınıf veya yapı bildiriminde bir yöntem `void` olmalı ve bir dönüş türüne sahip olmalıdır. Kullanma, `Conditional` blokların içine `#if…#endif` girme yöntemlerinden daha temiz, daha zarif ve daha az hataya açıktır.

Bir yöntemin `Conditional` birden çok özniteliği varsa, bir veya daha fazla koşullu sembol tanımlanırsa (semboller OR işleci kullanılarak mantıksal olarak birbirine bağlanır) yönteme çağrı bulunur. Aşağıdaki örnekte, bir yöntem `A` `B` çağrısıya neden olan veya bu çağrılardan birinin varlığı:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>Öznitelik sınıfları ile kullanma `Conditional`

Öznitelik, `Conditional` öznitelik sınıfı tanımına da uygulanabilir. Aşağıdaki örnekte, özel öznitelik `Documentation` yalnızca tanımlanmışsa `DEBUG` meta verilere bilgi ekler.

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>`Obsolete` özniteliği

Öznitelik `Obsolete` artık kullanım için önerilen bir kod öğesi işaretler. Eski işaretlenmiş bir varlığın kullanımı bir uyarı veya hata oluşturur. Öznitelik `Obsolete` tek kullanımlık bir özniteliktir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir. `Obsolete`<xref:System.ObsoleteAttribute>için bir takma addır.

Aşağıdaki örnekte `Obsolete` öznitelik sınıfa `A` ve yönteme `B.OldMethod`uygulanır. Öznitelik oluşturucu uygulanan ikinci bağımsız `B.OldMethod` değişken için `true`ayarlanmış olduğundan, bu yöntem derleyici hatasına neden olurken, sınıf `A` kullanarak sadece bir uyarı üretecektir. Ancak `B.NewMethod`arama, hiçbir uyarı veya hata üretir. Örneğin, önceki tanımlarla kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

Öznitelik oluşturucuya ilk bağımsız değişken olarak sağlanan dize, uyarı veya hatanın bir parçası olarak görüntülenir. Sınıf `A` için iki uyarı oluşturulur: biri sınıf başvuru bildirimi için, diğeri sınıf oluşturucusu için. Öznitelik `Obsolete` bağımsız değişkenler olmadan kullanılabilir, ancak bunun yerine ne kullanılacağı bir açıklama da dahil olmak üzere önerilir.

## <a name="attributeusage-attribute"></a>`AttributeUsage` özniteliği

Öznitelik, özel bir öznitelik sınıfının `AttributeUsage` nasıl kullanılabileceğini belirler. <xref:System.AttributeUsageAttribute>özel öznitelik tanımlarına uyguladığınız bir özniteliktir. Öznitelik, `AttributeUsage` aşağıdakileri denetlemenizi sağlar:

- Hangi program öğeleriöze uygulanabilir. Kullanımını kısıtlamadığınız sürece, aşağıdaki program öğelerinden herhangi biri için bir öznitelik uygulanabilir:
  - derleme
  - modül
  - alan
  - event
  - method
  - param
  - özellik
  - return
  - type
- Bir öznitelik birden çok kez tek bir program öğesine uygulanabilir olup olmadığını.
- Özniteliklerin türetilmiş sınıflar tarafından devralınmış olup olmadığı.

Varsayılan ayarlar açıkça uygulandığında aşağıdaki örnek gibi görünür:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

Bu örnekte, `NewAttribute` sınıf desteklenen herhangi bir program öğesine uygulanabilir. Ancak her varlık için yalnızca bir kez uygulanabilir. Öznitelik, taban sınıfa uygulandığında türetilmiş sınıflar tarafından devralınan.

Ve <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> bağımsız değişkenler isteğe bağlıdır, bu nedenle aşağıdaki kod aynı etkiye sahiptir:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

İlk <xref:System.AttributeUsageAttribute> bağımsız değişken numaralandırmanın <xref:System.AttributeTargets> bir veya daha fazla öğesi olmalıdır. Birden çok hedef türü, aşağıdaki örnekte görüldüğü gibi, OR işleciyle birlikte bağlanabilir:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

C# 7.3'ten başlayarak, öznitelikler otomatik olarak uygulanan bir özellik için özellik veya destek alanına uygulanabilir. Öznitelik, öznitelikte `field` belirtici belirtmediğiniz sürece özellik için geçerlidir. Her ikisi de aşağıdaki örnekte gösterilir:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<xref:System.AttributeUsageAttribute.AllowMultiple> Bağımsız değişken `true`ise, aşağıdaki örnekte gösterildiği gibi, ortaya çıkan öznitelik tek bir varlığa birden fazla kez uygulanabilir:

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

Bu durumda, `MultiUseAttribute` '' olarak `AllowMultiple` `true`ayarlandığı için tekrar tekrar uygulanabilir. Birden çok öznitelik uygulamak için gösterilen her iki biçim de geçerlidir.

<xref:System.AttributeUsageAttribute.Inherited> Ise, `false`o zaman öznitelik atfedilen bir sınıftan türetilen sınıflar tarafından devralınan değildir. Örneğin:

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

Bu durumda `NonInheritedAttribute` miras `DClass` yoluyla uygulanmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Öznitelikler](../../../standard/attributes/index.md)
- [Yansıma](../../programming-guide/concepts/reflection.md)
