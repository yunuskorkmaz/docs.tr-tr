---
title: 'C# ayrılmış öznitelikleri: koşullu, kullanımdan kalktı, AttributeUsage'
ms.date: 04/09/2020
description: Derleyici tarafından oluşturulan kodu etkilemek için bu öznitelikler derleyici tarafından yorumlanır
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021766"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>Ayrılmış öznitelikler: ConditionalAttribute, kullanımdan kaldırma Teattribute, AttributeUsageAttribute

Bu öznitelikler, kodunuzdaki öğelere uygulanabilir. Bunlar bu öğelere anlam anlam ekler. Derleyici, kodunuzu kullanarak geliştiricilerin çıktısını değiştirmek ve olası hataları raporlamak için bu anlamsal anlamları kullanır.

## <a name="conditional-attribute"></a>`Conditional` özniteliği

`Conditional`Özniteliği bir işlem ön işleme tanımlayıcısına bağımlı bir yöntemin yürütülmesini sağlar. `Conditional`Özniteliği için bir diğer addır <xref:System.Diagnostics.ConditionalAttribute> ve bir yönteme veya öznitelik sınıfına uygulanabilir.

Aşağıdaki örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı bırakmak için bir yönteme uygulanır:

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

`TRACE_ON`Tanımlayıcı tanımlanmamışsa, izleme çıktısı gösterilmez. Etkileşimli pencerede kendiniz için araştırma yapın.

`Conditional`Bu öznitelik, `DEBUG` Aşağıdaki örnekte gösterildiği gibi, genellikle hata ayıklama derlemeleri için izleme ve günlüğe kaydetme özelliklerini etkinleştirmek üzere tanımlayıcıda kullanılır:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, belirtilen ön işleme simgesinin varlığı veya yokluğu, çağrının eklenip eklenmeyeceğini veya atlanmadığını belirler. Sembol tanımlanmışsa, çağrı dahil edilir; Aksi takdirde, çağrı atlanır. Koşullu Yöntem bir sınıf veya yapı bildiriminde bir yöntem olmalıdır ve bir `void` dönüş türüne sahip olmalıdır. `Conditional`' Yi kullanarak temizleyici, daha zarif ve daha az hata, bloklar içindeki kapsayan metotlardan çok daha açıktır `#if…#endif` .

Bir yöntemde birden çok `Conditional` öznitelik varsa, bir veya daha fazla koşullu sembol tanımlanmışsa yönteme bir çağrı dahil edilir (semboller, or işleci kullanılarak mantıksal olarak birbirlerine bağlanır). Aşağıdaki örnekte, ya da `A` `B` bir yöntem çağrısında oluşur:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>`Conditional`Öznitelik sınıfları ile kullanma

`Conditional`Öznitelik, öznitelik sınıfı tanımına da uygulanabilir. Aşağıdaki örnekte, özel öznitelik `Documentation` yalnızca tanımlanmazsa meta verilere bilgi ekler `DEBUG` .

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>`Obsolete` özniteliği

`Obsolete`Öznitelik, artık kullanım için önerilmeyen bir kod öğesini işaretler. Kullanımdan kaldırılmış olarak işaretlenmiş bir varlığın kullanımı bir uyarı veya hata oluşturur. `Obsolete`Özniteliği tek kullanım özniteliğidir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir. `Obsolete` , için bir diğer addır <xref:System.ObsoleteAttribute> .

Aşağıdaki örnekte, `Obsolete` özniteliği sınıfa `A` ve yöntemine uygulanır `B.OldMethod` . Öğesine uygulanan öznitelik oluşturucusunun ikinci bağımsız değişkeni `B.OldMethod` olarak ayarlandığından `true` , bu yöntem bir derleyici hatasına neden olur, ancak sınıf kullanımı `A` yalnızca bir uyarı oluşturur. Ancak çağırma, `B.NewMethod` hiçbir uyarı veya hata üretir. Örneğin, önceki tanımlarla birlikte kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

Öznitelik oluşturucusuna ilk bağımsız değişken olarak girilen dize, uyarının veya hatanın bir parçası olarak görüntülenir. Sınıf için iki uyarı `A` oluşturulur: biri sınıf başvurusunun bildirimi ve diğeri sınıf oluşturucusu içindir. `Obsolete`Özniteliği bağımsız değişkenler olmadan kullanılabilir, ancak bunun yerine kullanılacak bir açıklama dahil edilmesi önerilir.

## <a name="attributeusage-attribute"></a>`AttributeUsage` özniteliği

`AttributeUsage`Özniteliği özel bir öznitelik sınıfının nasıl kullanılabileceğini belirler. <xref:System.AttributeUsageAttribute> , özel öznitelik tanımlarına uyguladığınız bir özniteliktir. `AttributeUsage`Özniteliği şunları denetlemenizi sağlar:

- Hangi program öğeleri özniteliği uygulanabilir olabilir. Kullanımını kısıtlamadığınız takdirde, aşağıdaki program öğelerinden birine bir öznitelik uygulanabilir:
  - derleme
  - modül
  - alan
  - event
  - method
  - larına
  - özellik
  - return
  - tür
- Bir özniteliğin tek bir program öğesine birden çok kez uygulanıp uygulanamayacağını belirtir.
- Özniteliklerin türetilmiş sınıflar tarafından devralınıp alınmayacağını belirtir.

Varsayılan ayarlar, açıkça uygulandığında aşağıdaki örneğe benzer şekilde görünür:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

Bu örnekte, `NewAttribute` sınıfı desteklenen herhangi bir program öğesine uygulanabilir. Ancak, her bir varlığa yalnızca bir kez uygulanabilir. Öznitelik, bir temel sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.

<xref:System.AttributeUsageAttribute.AllowMultiple>Ve <xref:System.AttributeUsageAttribute.Inherited> bağımsız değişkenleri isteğe bağlıdır, bu nedenle aşağıdaki kod aynı etkiye sahiptir:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

İlk <xref:System.AttributeUsageAttribute> bağımsız değişken, numaralandırmanın bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> . Aşağıdaki örnekte gösterildiği gibi birden çok hedef türü OR işleciyle birlikte bağlanabilir:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

C# 7,3 ' den başlayarak, öznitelikler bir otomatik uygulanan özelliğin özelliğine veya yedekleme alanına uygulanabilir. Özniteliği, özniteliğinde tanımlayıcı belirtmediğiniz müddetçe özelliği için geçerlidir `field` . Her ikisi de aşağıdaki örnekte gösterilmiştir:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<xref:System.AttributeUsageAttribute.AllowMultiple>Bağımsız değişken ise `true` , aşağıdaki örnekte gösterildiği gibi, sonuç özniteliği tek bir varlığa birden çok kez uygulanabilir:

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

Bu durumda, `MultiUseAttribute` olarak ayarlandığı için tekrar tekrar uygulanabilir `AllowMultiple` `true` . Birden çok özniteliği uygulamak için gösterilen her iki biçim de geçerlidir.

<xref:System.AttributeUsageAttribute.Inherited>İse `false` öznitelik, öznitelikli bir sınıftan türetilmiş sınıflar tarafından devralınmaz. Örneğin:

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

Bu durumda `NonInheritedAttribute` devralma aracılığıyla öğesine uygulanmaz `DClass` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Öznitelikler](../../../standard/attributes/index.md)
- [Yansıma](../../programming-guide/concepts/reflection.md)
