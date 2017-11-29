---
title: C# 7.1 yenilikler nelerdir?
description: "C# 7.1 içindeki yeni özelliklere genel bakış."
keywords: "C# dil tasarımında, 7.1, Visual Studio 2017,"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a>C# 7.1 yenilikler nelerdir?

C# 7.1, C# dili için ilk noktası sürümüdür. Artan sürüm tempoyla dil için işaretler. Her yeni özellik hazır olduğunda, yeni özelliklerin daha erken, ideal olarak kullanabilirsiniz. C# 7.1 derleyici dil belirtilen sürümüyle eşleşecek şekilde yapılandırma olanağını ekler. Bu, dil sürümlerini yükseltmek için karar araçları yükseltmeye karar ayırmanıza olanak sağlar.

C# 7.1 ekler [dil sürümü seçimi](#language-version-selection) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı.

Bu sürümdeki yeni diz özellikleri şunlardır:

* [`async``Main` yöntemi](#async-main)
  - Bir uygulama için giriş noktası olabilir `async` değiştiricisi.
* [`default`Sabit ifadeleri](#default-literal-expressions)
  - Hedef türü çıkarsanabileceği olduğunda, varsayılan değeri ifadelerinde varsayılan değişmez değer ifadeleri kullanabilirsiniz.
* [Çıkarsanan tanımlama grubu öğe adları](#inferred-tuple-element-names)
  - Başlığın öğeleri adlarını, çoğu durumda tanımlama grubu başlatılmasından çıkarsanabileceği.

Son olarak, derleyici iki seçenek vardır `/refout` ve `/refonly` denetleyen [başvuru derleme oluşturma](#reference-assembly-generation).

## <a name="language-version-selection"></a>Dil sürümü seçimi

C# Derleyici C# Visual Studio 2017 sürüm 15.3 veya .NET Core SDK 2.0 ile başlayan 7.1 destekler. Ancak, 7.1 özellikleri varsayılan olarak kapalıdır. 7.1 özellikleri etkinleştirmek için projeniz için dil sürümü ayarı değiştirmeniz gerekir.

Visual Studio'da, Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve seçin **özellikleri**. Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi. Açılır listede seçin **C# son alt sürüm (son)**, veya belirli bir sürümünü **C# 7.1** görüntü aşağıda gösterildiği gibi. `latest` Değeri, geçerli makineye en son alt sürüm kullanmak istediğiniz anlamına gelir. `C# 7.1` Yeni ikincil sürümleri bile sunulduktan sonra C# 7.1, kullanmak istediğiniz anlamına gelir.

![Dil sürümünü ayarlama](./media/csharp-7-1/advanced-build-settings.png)

Alternatif olarak, "csproj" dosyasını düzenleyin ve ekleyebilir veya aşağıdaki satırları değiştirin:

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Csproj dosyalarınızı güncelleştirmek için Visual Studio IDE kullanırsanız, IDE her yapı yapılandırması için ayrı düğüm oluşturur. Genellikle değerini aynı tüm yapı yapılandırmalarında ayarlamanız, ancak her yapı yapılandırması için açıkça ayarlamak veya bu ayarı değiştirdikten sonra "Tüm yapılandırmaları" seçmek gerekir. Aşağıdaki csproj dosyanızda görürsünüz:

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

İçin geçerli ayarları `LangVersion` öğesidir:

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

Özel dizeler `default` ve `latest` yapı, sırasıyla makinede en son birincil ve ikincil dil sürümleri çözmek.

Bu ayar, bir projede yeni dil özellikleri içerecek şekilde seçme gelen geliştirme ortamınızı yeni sürümlerini SDK ve araçlarını yükleme ayrıştırır. En son SDK'yı ve araçları, yapı makinenizde yükleyebilirsiniz. Her proje, derleme için belirli bir dil sürümünü kullanacak şekilde yapılandırılabilir.

## <a name="async-main"></a>Zaman uyumsuz ana

Bir *zaman uyumsuz ana* yöntemi kullanmanıza olanak sağlayan `await` içinde `Main` yöntemi.
Daha önce yazma gerekir:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Şimdi yazabilirsiniz:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Programınızı bir çıkış kodu varsa döndürmez, bildirebilirsiniz bir `Main` döndüren yöntemi bir <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Daha fazla bilgiyi ayrıntılar hakkında [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) konusu programlama kılavuzu.

## <a name="default-literal-expressions"></a>Varsayılan sabit ifadeleri

Varsayılan değişmez değer varsayılan değer ifadeleri yüklenene ifadelerini.
Bu ifade bir değişken varsayılan değere başlatır. Daha önce burada yazarsınız:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Sağ taraftaki başlatma türü artık atlayabilirsiniz:

```csharp
Func<string, bool> whereClause = default;
```

Üzerinde C# programlama kılavuzu konusundaki bu geliştirme hakkında daha fazla bilgiyi [varsayılan değeri ifadeleri](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Bu geliştirme, ayrıca bazı ayrıştırma kurallarının değiştirir [default anahtar sözcüğü](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Çıkarsanan tanımlama grubu öğe adları

Bu özellik, C# 7. 0'sunulan diziler özellikle küçük bir yeniliktir. Bir tanımlama grubu başlattığınızda birçok kez atama için sağ tarafında kullanılan değişkenler tanımlama grubu öğeleri için istediğiniz adları aynıdır:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Başlığın öğeleri adları C# 7.1 düzeninde başlatmak için kullanılan değişkenlerden çıkarsanabileceği:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Bu özellik hakkında daha fazla bilgiyi [diziler](../tuples.md) konu.

## <a name="reference-assembly-generation"></a>Başvuru derleme oluşturma

Üreten iki yeni derleyici seçenekleri vardır *yalnızca başvuru derlemeleri*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) ve [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Bağlantılı konulardan Bu seçenekler ve daha ayrıntılı başvuru derlemeleri açıklamaktadır.
