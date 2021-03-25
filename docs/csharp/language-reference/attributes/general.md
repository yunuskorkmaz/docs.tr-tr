---
title: 'C# ayrılmış öznitelikleri: çeşitli'
ms.date: 03/18/2021
description: 'Derleyici tarafından oluşturulan kodu etkileyen öznitelikler hakkında bilgi edinin: koşullu, Kullanımdan kaldırılmış, AttributeUsage, Modulebaşlatıcı ve Skiplocalsinıt öznitelikleri.'
ms.openlocfilehash: 6b8cda658ec5b3f81a7f903d8cadae0fe30e8ac2
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111328"
---
# <a name="reserved-attributes-miscellaneous"></a>Ayrılmış öznitelikler: çeşitli

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

<xref:System.AttributeUsageAttribute.Inherited>İse `false` öznitelik, öznitelikli bir sınıftan türetilmiş sınıflar tarafından devralınmaz. Örnek:

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

Bu durumda `NonInheritedAttribute` devralma aracılığıyla öğesine uygulanmaz `DClass` .

## <a name="moduleinitializer-attribute"></a>`ModuleInitializer` özniteliği

C# 9 ' dan itibaren `ModuleInitializer` öznitelik, derleme yüklendiğinde çalışma zamanının çağırdığı bir yöntemi işaretler. `ModuleInitializer` , için bir diğer addır <xref:System.Runtime.CompilerServices.ModuleInitializerAttribute> .

`ModuleInitializer`Özniteliği yalnızca şu şekilde bir yönteme uygulanabilir:

* Statiktir.
* Parametresiz.
* `void` döndürür.
* ,, Veya içeren modülünden erişilebilir `internal` `public` .
* Genel bir yöntem değildir.
* Genel bir sınıfta içerilmiyor.
* Yerel bir işlev değil.

`ModuleInitializer`Özniteliği birden çok yönteme uygulanabilir. Bu durumda, çalışma zamanının onları çağıran sıra belirleyici olur ancak belirtilmez.

Aşağıdaki örnekte, birden çok modül başlatıcısı yönteminin kullanımı gösterilmektedir. `Init1`Ve `Init2` yöntemleri daha önce çalışır `Main` ve her biri özelliğine bir dize ekler `Text` . Bu nedenle `Main` , özelliği çalıştırıldığında `Text` her iki Başlatıcı yönteminden dizeler zaten vardır.

:::code language="csharp" source="snippets/ModuleInitializerExampleMain.cs" :::

:::code language="csharp" source="snippets/ModuleInitializerExampleModule.cs" :::

Kaynak kodu oluşturanlar bazen başlatma kodu üretmemelidir. Modül başlatıcıları, bu kodun bulunması için standart bir yer sağlar.

## <a name="skiplocalsinit-attribute"></a>`SkipLocalsInit` özniteliği

C# 9 ' dan itibaren `SkipLocalsInit` öznitelik, derleyicinin `.locals init` meta veriye yayırken bayrak değiştirmesini engeller. `SkipLocalsInit`Özniteliği tek kullanılan bir özniteliktir ve bir metoda, özelliğe, bir sınıfa, yapıya, arabirime veya modüle uygulanabilir ancak bir derlemeye uygulanamaz. `SkipLocalsInit` , için bir diğer addır <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute> .

`.locals init`Bayrak, clr 'nin bir yöntemde belirtilen tüm yerel değişkenleri varsayılan değerlerine başlatmasını sağlar. Derleyici aynı zamanda bir değeri bir değere atamadan önce hiçbir şekilde hiç bir değişken kullandığınızdan emin olduğundan, `.locals init` genellikle gerekli değildir. Ancak, yığın üzerinde bir dizi ayırmak için [stackalloc](../operators/stackalloc.md) kullandığınızda gibi, ek sıfır başlatma bazı senaryolarda ölçülebilir performans etkisine sahip olabilir. Bu durumlarda `SkipLocalsInit` özniteliği ekleyebilirsiniz. Bir yönteme doğrudan uygulanırsa öznitelik, Lambdalar ve yerel işlevler dahil olmak üzere bu yöntemi ve tüm iç içe geçmiş işlevleri etkiler. Bir tür veya modüle uygulanmışsa, içinde iç içe geçmiş tüm yöntemleri etkiler. Bu öznitelik soyut yöntemleri etkilemez, ancak uygulama için oluşturulan kodu etkiler.

Bu öznitelik, [AllowUnsafeBlocks](../compiler-options/language.md#allowunsafeblocks) derleyici seçeneğini gerektiriyor. Bu, bazı durumlarda kod atanmamış belleği (örneğin, başlatılmamış yığına ayrılan bellekten okuma) görüntüleyebileceğinden emin olmak için kullanılır.

Aşağıdaki örnek, `SkipLocalsInit` tarafından kullanılan bir yöntemde özniteliğinin etkisini gösterir `stackalloc` . Bu yöntem, tamsayılar dizisi ayrıldığında bellekte ne olduğunu gösterir.

:::code language="csharp" source="snippets/SkipLocalsInitExample.cs" id="ReadUninitializedMemory":::

Bu kodu kendiniz denemek için `AllowUnsafeBlocks` *. csproj* dosyanızdaki derleyici seçeneğini ayarlayın:

```xml
<PropertyGroup>
  ...
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Öznitelikler](../../../standard/attributes/index.md)
- [Yansıma](../../programming-guide/concepts/reflection.md)
