---
title: Konsol günlük biçimlendirme
description: Kullanılabilir konsol günlük biçimlendirmesini kullanmayı veya .NET uygulamalarınız için özel günlük biçimlendirmesini uygulamayı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 12/17/2020
ms.openlocfilehash: 0ec8fc2018febe4273aa646d1682be197933f925
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700821"
---
# <a name="console-log-formatting"></a><span data-ttu-id="72241-103">Konsol günlük biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="72241-103">Console log formatting</span></span>

<span data-ttu-id="72241-104">.NET 5 ' te, ad alanındaki konsol günlüklerine özel biçimlendirme desteği eklenmiştir `Microsoft.Extensions.Logging.Console` .</span><span class="sxs-lookup"><span data-stu-id="72241-104">In .NET 5, support for custom formatting was added to console logs in the `Microsoft.Extensions.Logging.Console` namespace.</span></span> <span data-ttu-id="72241-105">Önceden tanımlanmış üç biçimlendirme seçeneği mevcuttur: [`Simple`](#simple) , [`Systemd`](#systemd) , ve [`Json`](#json) .</span><span class="sxs-lookup"><span data-stu-id="72241-105">There are three predefined formatting options available: [`Simple`](#simple), [`Systemd`](#systemd), and [`Json`](#json).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72241-106">Daha önce, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> istenen günlük biçimini seçmeye izin verilen numaralandırma, ya da `Default` olarak da bilinen tek satır olan insanlar okunabilir `Systemd` .</span><span class="sxs-lookup"><span data-stu-id="72241-106">Previously, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> enum allowed for selecting the desired log format, either human readable which was the `Default`, or single line which is also known as `Systemd`.</span></span> <span data-ttu-id="72241-107">Ancak **bunlar özelleştirilemez ve** artık kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="72241-107">However, these were **not** customizable, and are now deprecated.</span></span>

<span data-ttu-id="72241-108">Bu makalede, konsol günlüğü formatlayıcıları hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="72241-108">In this article, you will learn about console log formatters.</span></span> <span data-ttu-id="72241-109">Örnek kaynak kodu şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="72241-109">The sample source code demonstrates how to:</span></span>

- <span data-ttu-id="72241-110">Yeni bir biçimlendirici Kaydet</span><span class="sxs-lookup"><span data-stu-id="72241-110">Register a new formatter</span></span>
- <span data-ttu-id="72241-111">Kullanılacak kayıtlı bir biçimlendirici seçin</span><span class="sxs-lookup"><span data-stu-id="72241-111">Select a registered formatter to use</span></span>
  - <span data-ttu-id="72241-112">Kod ya da [yapılandırma](configuration.md) üzerinden</span><span class="sxs-lookup"><span data-stu-id="72241-112">Either through code, or [configuration](configuration.md)</span></span>
- <span data-ttu-id="72241-113">Özel biçimlendirici uygulama</span><span class="sxs-lookup"><span data-stu-id="72241-113">Implement a custom formatter</span></span>
  - <span data-ttu-id="72241-114">Yapılandırmayı Güncelleştirme aracılığıyla <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span><span class="sxs-lookup"><span data-stu-id="72241-114">Update configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span></span>
  - <span data-ttu-id="72241-115">Özel renk biçimlendirmesini etkinleştir</span><span class="sxs-lookup"><span data-stu-id="72241-115">Enable custom color formatting</span></span>

## <a name="register-formatter"></a><span data-ttu-id="72241-116">Biçimlendirici Kaydet</span><span class="sxs-lookup"><span data-stu-id="72241-116">Register formatter</span></span>

<span data-ttu-id="72241-117">[ `Console` Günlüğe kaydetme sağlayıcısında](logging-providers.md#console) birkaç önceden tanımlı biçim vardır ve kendi özel biçimlendiricinizi yazma özelliğini ortaya koyar.</span><span class="sxs-lookup"><span data-stu-id="72241-117">The [`Console` logging provider](logging-providers.md#console) has several predefined formatters, and exposes the ability to author your own custom formatter.</span></span> <span data-ttu-id="72241-118">Kullanılabilir formatlayıcıları kaydetmek için ilgili `Add{Type}Console` genişletme yöntemini kullanın:</span><span class="sxs-lookup"><span data-stu-id="72241-118">To register any of the available formatters, use the corresponding `Add{Type}Console` extension method:</span></span>

| <span data-ttu-id="72241-119">Kullanılabilir türler</span><span class="sxs-lookup"><span data-stu-id="72241-119">Available types</span></span> | <span data-ttu-id="72241-120">Kayıt türü yöntemi</span><span class="sxs-lookup"><span data-stu-id="72241-120">Method to register type</span></span> |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a><span data-ttu-id="72241-121">Basit</span><span class="sxs-lookup"><span data-stu-id="72241-121">Simple</span></span>

<span data-ttu-id="72241-122">`Simple`Konsol biçimlendirici 'yı kullanmak için şunu ile kaydedin `AddSimpleConsole` :</span><span class="sxs-lookup"><span data-stu-id="72241-122">To use the `Simple` console formatter, register it with `AddSimpleConsole`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

<span data-ttu-id="72241-123">Önceki örnek kaynak kodunda, <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> biçimlendirici kaydettirildi.</span><span class="sxs-lookup"><span data-stu-id="72241-123">In the preceding sample source code, the <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> formatter was registered.</span></span> <span data-ttu-id="72241-124">Yalnızca her bir günlük iletisindeki zaman ve günlük düzeyi gibi bilgileri kaydırabilme olanağı sağlar, ancak Ayrıca iletilerin ANSI renk ekleme ve girintileme için de izin verir.</span><span class="sxs-lookup"><span data-stu-id="72241-124">It provides logs with the ability to not only wrap information such as time and log level in each log message, but also allows for ANSI color embedding and indentation of messages.</span></span>

### <a name="systemd"></a><span data-ttu-id="72241-125">Systemd</span><span class="sxs-lookup"><span data-stu-id="72241-125">Systemd</span></span>

<span data-ttu-id="72241-126"><xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>Konsol günlükçüsü:</span><span class="sxs-lookup"><span data-stu-id="72241-126">The <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> console logger:</span></span>

- <span data-ttu-id="72241-127">"Syslog" günlük düzeyi biçimini ve önem derecelerine kullanır</span><span class="sxs-lookup"><span data-stu-id="72241-127">Uses the "Syslog" log level format and severities</span></span>
- <span data-ttu-id="72241-128">İletileri renklerle **biçimlendirmez**</span><span class="sxs-lookup"><span data-stu-id="72241-128">Does **not** format messages with colors</span></span>
- <span data-ttu-id="72241-129">İletileri her zaman tek bir satırda günlüğe kaydeder</span><span class="sxs-lookup"><span data-stu-id="72241-129">Always logs messages in a single line</span></span>

<span data-ttu-id="72241-130">Bu, genellikle konsol günlüğünü kullanan kapsayıcılar için yararlıdır `Systemd` .</span><span class="sxs-lookup"><span data-stu-id="72241-130">This is commonly useful for containers, which often make use of `Systemd` console logging.</span></span> <span data-ttu-id="72241-131">.NET 5 ile `Simple` konsol günlükçüsü, tek bir satırda oturum açan ve ayrıca daha önceki bir örnekte gösterildiği gibi renklerin devre dışı bırakılmasına izin veren bir Compact sürümü de sağlar.</span><span class="sxs-lookup"><span data-stu-id="72241-131">With .NET 5, the `Simple` console logger also enables a compact version that logs in a single line, and also allows for disabling colors as shown in an earlier sample.</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a><span data-ttu-id="72241-132">Json</span><span class="sxs-lookup"><span data-stu-id="72241-132">Json</span></span>

<span data-ttu-id="72241-133">Günlükleri JSON biçiminde yazmak için `Json` konsol biçimlendiricisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72241-133">To write logs in a JSON format, the `Json` console formatter is used.</span></span> <span data-ttu-id="72241-134">Örnek kaynak kodu bir ASP.NET Core uygulamasının nasıl kaydedebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72241-134">The sample source code shows how an ASP.NET Core app might register it.</span></span> <span data-ttu-id="72241-135">Şablonu kullanarak `webapp` , [DotNet yeni](../tools/dotnet-new.md) komutuyla yeni bir ASP.NET Core uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="72241-135">Using the `webapp` template, create a new ASP.NET Core app with the [dotnet new](../tools/dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

<span data-ttu-id="72241-136">Uygulamayı çalıştırırken, şablon kodunu kullanarak aşağıdaki varsayılan günlük biçimini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="72241-136">When running the app, using the template code, you get the default log format below:</span></span>

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

<span data-ttu-id="72241-137">Varsayılan olarak `Simple` konsol günlük biçimlendiricisi varsayılan yapılandırmayla seçilir.</span><span class="sxs-lookup"><span data-stu-id="72241-137">By default, the `Simple` console log formatter is selected with default configuration.</span></span> <span data-ttu-id="72241-138">Bunu `AddJsonConsole` *program.cs* içinde çağırarak değiştirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72241-138">You change this by calling `AddJsonConsole` in the *Program.cs*:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

<span data-ttu-id="72241-139">Uygulamayı bir daha çalıştırın, yukarıdaki değişiklik ile günlük iletisi artık JSON olarak biçimlendirilir:</span><span class="sxs-lookup"><span data-stu-id="72241-139">Run the app again, with the above change, the log message is now formatted as JSON:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> <span data-ttu-id="72241-140">`Json`Konsol biçimlendiricisi, varsayılan olarak her iletiyi tek bir satırda günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="72241-140">The `Json` console formatter, by default, logs each message in a single line.</span></span> <span data-ttu-id="72241-141">Biçimlendirici yapılandırılırken daha okunaklı olması için, <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="72241-141">In order to make it more readable while configuring the formatter, set <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> to `true`.</span></span>

## <a name="set-formatter-with-configuration"></a><span data-ttu-id="72241-142">Biçimlendirici yapılandırma ile ayarla</span><span class="sxs-lookup"><span data-stu-id="72241-142">Set formatter with configuration</span></span>

<span data-ttu-id="72241-143">Önceki örneklerde, bir biçimlendirici programlı bir şekilde nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72241-143">The previous samples have shown how to register a formatter programmatically.</span></span> <span data-ttu-id="72241-144">Alternatif olarak, bu [yapılandırma](configuration.md)ile yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="72241-144">Alternatively, this can be done with [configuration](configuration.md).</span></span> <span data-ttu-id="72241-145">Önceki Web uygulaması örnek kaynak kodunu göz önünde bulundurun, Program.cs dosyasında çağırmak yerine dosyayı *appsettings.js* güncelleştirirseniz `ConfigureLogging` aynı sonucu elde edebilirsiniz  .</span><span class="sxs-lookup"><span data-stu-id="72241-145">Consider the previous web application sample source code, if you update the *appsettings.json* file rather than calling `ConfigureLogging` in the *Program.cs* file, you could get the same outcome.</span></span> <span data-ttu-id="72241-146">Güncelleştirilmiş `appsettings.json` Dosya, biçimlendirici şu şekilde yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="72241-146">The updated `appsettings.json` file would configure the formatter as follows:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

<span data-ttu-id="72241-147">Ayarlanması gereken iki anahtar değeri `"FormatterName"` ve ' dir `"FormatterOptions"` .</span><span class="sxs-lookup"><span data-stu-id="72241-147">The two key values that need to be set are `"FormatterName"` and `"FormatterOptions"`.</span></span> <span data-ttu-id="72241-148">İçin değer kümesine sahip bir biçimlendirici `"FormatterName"` zaten kaydedilmişse, bu biçimlendirici seçilir ve özellikleri düğüm içinde bir anahtar olarak sağlandıkları sürece yapılandırılabilir `"FormatterOptions"` .</span><span class="sxs-lookup"><span data-stu-id="72241-148">If a formatter with the value set for `"FormatterName"` is already registered, that formatter is selected, and its properties can be configured as long as they are provided as a key inside the `"FormatterOptions"` node.</span></span> <span data-ttu-id="72241-149">Önceden tanımlanmış biçimlendirici adları şu şekilde ayrılmıştır <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> :</span><span class="sxs-lookup"><span data-stu-id="72241-149">The predefined formatter names are reserved under <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames>:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a><span data-ttu-id="72241-150">Özel biçimlendirici uygulama</span><span class="sxs-lookup"><span data-stu-id="72241-150">Implement a custom formatter</span></span>

<span data-ttu-id="72241-151">Özel bir biçimlendirici uygulamak için şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="72241-151">To implement a custom formatter, you need to:</span></span>

- <span data-ttu-id="72241-152">İçin bir alt sınıf oluşturun <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> , bu özel biçimlendiricisi temsil eder</span><span class="sxs-lookup"><span data-stu-id="72241-152">Create a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter>, this represents your custom formatter</span></span>
- <span data-ttu-id="72241-153">Özel biçimlendirici hesabınızı kaydetme</span><span class="sxs-lookup"><span data-stu-id="72241-153">Register your custom formatter with</span></span>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

<span data-ttu-id="72241-154">Bunu sizin için işlemek üzere bir genişletme yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="72241-154">Create an extension method to handle this for you:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

<span data-ttu-id="72241-155">, `CustomOptions` Aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="72241-155">The `CustomOptions` are defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

<span data-ttu-id="72241-156">Yukarıdaki kodda, seçenekleri öğesinin bir alt sınıfıdır <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> .</span><span class="sxs-lookup"><span data-stu-id="72241-156">In the preceding code, the options are a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>.</span></span>

<span data-ttu-id="72241-157">`AddConsoleFormatter`API:</span><span class="sxs-lookup"><span data-stu-id="72241-157">The `AddConsoleFormatter` API:</span></span>

- <span data-ttu-id="72241-158">Bir alt sınıfını kaydeder `ConsoleFormatter`</span><span class="sxs-lookup"><span data-stu-id="72241-158">Registers a subclass of `ConsoleFormatter`</span></span>
- <span data-ttu-id="72241-159">Tanıtıcı yapılandırma:</span><span class="sxs-lookup"><span data-stu-id="72241-159">Handles configuration:</span></span>
  - <span data-ttu-id="72241-160">, [Seçenekler düzenine](options.md)ve [ıoptionsmonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) arabirimine göre güncelleştirmeleri eşleştirmek için bir değişiklik belirteci kullanır</span><span class="sxs-lookup"><span data-stu-id="72241-160">Uses a change token to synchronize updates, based on the [options pattern](options.md), and the [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) interface</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

<span data-ttu-id="72241-161">Bir `CustomerFormatter` alt sınıfı tanımlayın `ConsoleFormatter` :</span><span class="sxs-lookup"><span data-stu-id="72241-161">Define a `CustomerFormatter` subclass of `ConsoleFormatter`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

<span data-ttu-id="72241-162">Yukarıdaki `CustomFormatter.Write<TState>` API, her günlük iletisi etrafında hangi metnin sarmalanacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="72241-162">The preceding `CustomFormatter.Write<TState>` API dictates what text gets wrapped around each log message.</span></span> <span data-ttu-id="72241-163">Bir standart `ConsoleFormatter` , en az kapsam, zaman damgası ve önem düzeyi olan günlüklerin etrafında kaydırabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="72241-163">A standard `ConsoleFormatter` should be able to wrap around scopes, time stamps, and severity level of logs at a minimum.</span></span> <span data-ttu-id="72241-164">Ayrıca, günlük iletilerinde ANSI renklerini kodlayabilir ve istenen girintileri de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72241-164">Additionally, you can encode ANSI colors in the log messages, and provide desired indentations as well.</span></span> <span data-ttu-id="72241-165">Uygulamasının `CustomFormatter.Write<TState>` Bu özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="72241-165">The implementation of the `CustomFormatter.Write<TState>` lacks these capabilities.</span></span>

<span data-ttu-id="72241-166">Biçimlendirmeyi daha fazla özelleştirme konusunda daha fazla bilgi için bkz. ad alanındaki mevcut uygulamalar `Microsoft.Extensions.Logging.Console` :</span><span class="sxs-lookup"><span data-stu-id="72241-166">For inspiration on further customizing formatting, see the existing implementations in the `Microsoft.Extensions.Logging.Console` namespace:</span></span>

- <span data-ttu-id="72241-167">[Simpleconsoleformatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).</span><span class="sxs-lookup"><span data-stu-id="72241-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).</span></span>
- [<span data-ttu-id="72241-168">SystemdConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="72241-168">SystemdConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [<span data-ttu-id="72241-169">JsonConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="72241-169">JsonConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a><span data-ttu-id="72241-170">Özel renk biçimlendirmesi Uygula</span><span class="sxs-lookup"><span data-stu-id="72241-170">Implement custom color formatting</span></span>

<span data-ttu-id="72241-171">Özel günlük biçimlendiricinizdeki renk yeteneklerini doğru bir şekilde etkinleştirmek için, ' yi, <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> günlüklerde renkleri etkinleştirmek faydalı olabilecek bir özelliğe sahip olacak şekilde genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72241-171">In order to properly enable color capabilities in your custom logging formatter, you can extend the <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> as it has a <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> property that can be useful for enabling colors in logs.</span></span>

<span data-ttu-id="72241-172">Şu `CustomColorOptions` kaynaktan türetilen bir oluştur `SimpleConsoleFormatterOptions` :</span><span class="sxs-lookup"><span data-stu-id="72241-172">Create a `CustomColorOptions` that derives from `SimpleConsoleFormatterOptions`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

<span data-ttu-id="72241-173">Daha sonra, `TextWriterExtensions` biçimlendirilen günlük ILETILERINDE ANSI kodlu renkleri kolay bir şekilde katıştırmaya izin veren bir sınıfta bazı uzantı yöntemlerini yazın:</span><span class="sxs-lookup"><span data-stu-id="72241-173">Next, write some extension methods in a `TextWriterExtensions` class that allow for conveniently embedding ANSI coded colors within formatted log messages:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

<span data-ttu-id="72241-174">Özel renkleri uygulamayı işleyen özel bir renk biçimlendiricisi aşağıdaki gibi tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="72241-174">A custom color formatter that handles applying custom colors could be defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

<span data-ttu-id="72241-175">Uygulamayı çalıştırdığınızda Günlükler olduğunda `CustomPrefix` iletiyi yeşil renkte gösterir `FormatterOptions.ColorBehavior` `Enabled` .</span><span class="sxs-lookup"><span data-stu-id="72241-175">When you run the application, the logs will show the `CustomPrefix` message in the color green when `FormatterOptions.ColorBehavior` is `Enabled`.</span></span>

> [!NOTE]
> <span data-ttu-id="72241-176">Ne zaman, <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> `Disabled` günlük iletileri, günlük iletileri IÇINDEKI gömülü ANSI renk kodlarını _yorumlamaz_ .</span><span class="sxs-lookup"><span data-stu-id="72241-176">When <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> is `Disabled`, log messages do _not_ interpret embedded ANSI color codes within log messages.</span></span> <span data-ttu-id="72241-177">Bunun yerine, ham iletiyi alırlar.</span><span class="sxs-lookup"><span data-stu-id="72241-177">Instead, they output the raw message.</span></span> <span data-ttu-id="72241-178">Örneğin, aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="72241-178">For example, consider the following:</span></span>
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> <span data-ttu-id="72241-179">Bu, tam dizeyi çıktılar ve _renklendirilmez_ .</span><span class="sxs-lookup"><span data-stu-id="72241-179">This would output the verbatim string, and it is _not_ colorized.</span></span>
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a><span data-ttu-id="72241-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72241-180">See also</span></span>

- [<span data-ttu-id="72241-181">.NET oturumu açma</span><span class="sxs-lookup"><span data-stu-id="72241-181">Logging in .NET</span></span>](logging.md)
- [<span data-ttu-id="72241-182">.NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama</span><span class="sxs-lookup"><span data-stu-id="72241-182">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="72241-183">.NET 'te yüksek performanslı günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="72241-183">High-performance logging in .NET</span></span>](high-performance-logging.md)
