---
title: JSON serileştirme-.NET için özel dönüştürücüler yazma
description: Ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturmayı öğrenin System.Text.Json .
ms.date: 01/22/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 1a13fe4e4717764130d05131969379de8a913f48
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583767"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="f1482-103">.NET 'teki JSON serileştirme (sıralama) için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="f1482-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="f1482-104">Bu makalede, ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturma işlemi gösterilmektedir <xref:System.Text.Json> .</span><span class="sxs-lookup"><span data-stu-id="f1482-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="f1482-105">Uygulamasına giriş için `System.Text.Json` bkz. [.net 'te JSON serileştirme ve seri durumdan çıkarma](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="f1482-105">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="f1482-106">*Dönüştürücü* bir nesneyi veya BIR değeri JSON öğesine veya bir değere dönüştüren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f1482-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="f1482-107">`System.Text.Json`Ad alanı, JavaScript temel elemanlarına eşleyen en basit türlerin yerleşik Dönüştürücülerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f1482-107">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="f1482-108">Özel dönüştürücüler yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1482-108">You can write custom converters:</span></span>

* <span data-ttu-id="f1482-109">Yerleşik dönüştürücünün varsayılan davranışını geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="f1482-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="f1482-110">Örneğin, `DateTime` değerlerin aa/gg/yyyy biçimiyle temsil olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1482-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format.</span></span> <span data-ttu-id="f1482-111">Varsayılan olarak, RFC 3339 profili de dahil olmak üzere ISO 8601-1:2019 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f1482-111">By default, ISO 8601-1:2019 is supported, including the RFC 3339 profile.</span></span> <span data-ttu-id="f1482-112">Daha fazla bilgi için, bkz. [' de System.Text.Json DateTime ve DateTimeOffset desteği ](../datetime/system-text-json-support.md).</span><span class="sxs-lookup"><span data-stu-id="f1482-112">For more information, see [DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).</span></span>
* <span data-ttu-id="f1482-113">Özel bir değer türünü desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="f1482-113">To support a custom value type.</span></span> <span data-ttu-id="f1482-114">Örneğin, bir `PhoneNumber` struct.</span><span class="sxs-lookup"><span data-stu-id="f1482-114">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="f1482-115">Ayrıca, `System.Text.Json` geçerli sürüme dahil olmayan işlevlerle özelleştirmek veya genişletmek için özel dönüştürücüler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1482-115">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="f1482-116">Bu makalenin ilerleyen bölümlerinde aşağıdaki senaryolar ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="f1482-116">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="f1482-117">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f1482-117">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f1482-118">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f1482-118">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f1482-119">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f1482-119">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="f1482-120">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f1482-120">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f1482-121">[Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="f1482-121">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="f1482-122">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f1482-122">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f1482-123">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f1482-123">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

<span data-ttu-id="f1482-124">Özel bir dönüştürücü için yazdığınız kodda, yeni örnekleri kullanmaya yönelik önemli performans cezası hakkında dikkat edin <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="f1482-124">In the code you write for a custom converter, be aware of the substantial performance penalty for using new <xref:System.Text.Json.JsonSerializerOptions> instances.</span></span> <span data-ttu-id="f1482-125">Daha fazla bilgi için bkz. [JsonSerializerOptions örneklerini yeniden kullanma](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span><span class="sxs-lookup"><span data-stu-id="f1482-125">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

<span data-ttu-id="f1482-126">Visual Basic, özel dönüştürücüler yazmak için kullanılamaz, ancak C# kitaplıklarında uygulanan dönüştürücüler çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f1482-126">Visual Basic can't be used to write custom converters but can call converters that are implemented in C# libraries.</span></span> <span data-ttu-id="f1482-127">Daha fazla bilgi için bkz. [Visual Basic desteği](system-text-json-how-to.md#visual-basic-support).</span><span class="sxs-lookup"><span data-stu-id="f1482-127">For more information, see [Visual Basic support](system-text-json-how-to.md#visual-basic-support).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="f1482-128">Özel dönüştürücü desenleri</span><span class="sxs-lookup"><span data-stu-id="f1482-128">Custom converter patterns</span></span>

<span data-ttu-id="f1482-129">Özel dönüştürücü oluşturmak için iki desen vardır: temel desen ve fabrika düzeni.</span><span class="sxs-lookup"><span data-stu-id="f1482-129">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="f1482-130">Fabrika deseninin türü `Enum` veya açık genel türleri işleyen dönüştürücüler içindir.</span><span class="sxs-lookup"><span data-stu-id="f1482-130">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="f1482-131">Temel model, genel olmayan ve kapalı genel türler içindir.</span><span class="sxs-lookup"><span data-stu-id="f1482-131">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="f1482-132">Örneğin, aşağıdaki türler için dönüştürücüler fabrika deseninin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f1482-132">For example, converters for the following types require the factory pattern:</span></span>

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

<span data-ttu-id="f1482-133">Temel model tarafından işlenebilen türlerin bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f1482-133">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

<span data-ttu-id="f1482-134">Temel model, bir türü işleyebileceğini bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1482-134">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="f1482-135">Fabrika stili, çalışma zamanında, belirli bir türün gerekli olduğunu ve uygun dönüştürücüyü dinamik olarak oluşturduğunu belirleyen bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1482-135">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="f1482-136">Örnek temel dönüştürücü</span><span class="sxs-lookup"><span data-stu-id="f1482-136">Sample basic converter</span></span>

<span data-ttu-id="f1482-137">Aşağıdaki örnek, varolan bir veri türü için varsayılan Serileştirmeyi geçersiz kılan bir dönüştürücütür.</span><span class="sxs-lookup"><span data-stu-id="f1482-137">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="f1482-138">Dönüştürücü özellikler için aa/gg/yyyy biçimini kullanır `DateTimeOffset` .</span><span class="sxs-lookup"><span data-stu-id="f1482-138">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="f1482-139">Örnek fabrika deseninin Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="f1482-139">Sample factory pattern converter</span></span>

<span data-ttu-id="f1482-140">Aşağıdaki kod ile birlikte çalışarak özel bir dönüştürücüyü gösterir `Dictionary<Enum,TValue>` .</span><span class="sxs-lookup"><span data-stu-id="f1482-140">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="f1482-141">İlk genel tür parametresi olduğundan ve ikincisi açık olduğundan, kod fabrika düzeniyle uyar `Enum` .</span><span class="sxs-lookup"><span data-stu-id="f1482-141">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="f1482-142">`CanConvert`Yöntemi `true` yalnızca, bir türü olan, yalnızca `Dictionary` iki genel parametre içeren için döndürür `Enum` .</span><span class="sxs-lookup"><span data-stu-id="f1482-142">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="f1482-143">İç dönüştürücü, için çalışma zamanında hangi türün sağlandığını işlemek üzere mevcut bir dönüştürücüyü alır `TValue` .</span><span class="sxs-lookup"><span data-stu-id="f1482-143">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="f1482-144">Yukarıdaki kod, bu makalede daha sonra [dize olmayan anahtarla destek sözlüğünde](#support-dictionary-with-non-string-key) gösterilenle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f1482-144">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="f1482-145">Temel kalıbı izlemeye yönelik adımlar</span><span class="sxs-lookup"><span data-stu-id="f1482-145">Steps to follow the basic pattern</span></span>

<span data-ttu-id="f1482-146">Aşağıdaki adımlarda, temel kalıbı izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f1482-146">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="f1482-147">Öğesinden türetilen, <xref:System.Text.Json.Serialization.JsonConverter%601> `T` seri hale getirilecek ve seri durumdan çıkarılacak bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f1482-147">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="f1482-148">`Read`Gelen JSON serisini kaldırmak ve türe dönüştürmek için yöntemini geçersiz kılın `T` .</span><span class="sxs-lookup"><span data-stu-id="f1482-148">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="f1482-149"><xref:System.Text.Json.Utf8JsonReader>JSON 'ı okumak için yöntemine geçirilen öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1482-149">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span> <span data-ttu-id="f1482-150">Seri hale getirici geçerli JSON kapsamının tüm verilerini geçirdiğinde kısmi verilerin işlenmesine endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f1482-150">You don't have to worry about handling partial data, as the serializer passes all the data for the current JSON scope.</span></span> <span data-ttu-id="f1482-151"><xref:System.Text.Json.Utf8JsonReader.Skip%2A> <xref:System.Text.Json.Utf8JsonReader.TrySkip%2A> Bu nedenle, bu döndürmeleri çağırmak veya doğrulamak gerekli değildir <xref:System.Text.Json.Utf8JsonReader.Read%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="f1482-151">So it isn't necessary to call <xref:System.Text.Json.Utf8JsonReader.Skip%2A> or <xref:System.Text.Json.Utf8JsonReader.TrySkip%2A> or to validate that <xref:System.Text.Json.Utf8JsonReader.Read%2A> returns `true`.</span></span>
* <span data-ttu-id="f1482-152">`Write`Türündeki gelen nesneyi seri hale getirmek için yöntemini geçersiz kılın `T` .</span><span class="sxs-lookup"><span data-stu-id="f1482-152">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="f1482-153"><xref:System.Text.Json.Utf8JsonWriter>JSON yazmak için yöntemine geçirilen öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1482-153">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="f1482-154">`CanConvert`Yöntemi yalnızca gerektiğinde geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="f1482-154">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="f1482-155">Varsayılan uygulama, `true` dönüştürülecek tür tür olduğunda döndürür `T` .</span><span class="sxs-lookup"><span data-stu-id="f1482-155">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="f1482-156">Bu nedenle, yalnızca türü destekleyen dönüştürücüler `T` Bu yöntemi geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1482-156">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="f1482-157">Bu yöntemi geçersiz kılmanın gerekli olduğu dönüştürücünün bir örneği için, bu makalenin ilerleyen kısımlarında yer alan [polimorfik serisini kaldırma](#support-polymorphic-deserialization) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f1482-157">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="f1482-158">[Yerleşik dönüştürücüler kaynak koduna](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) , özel dönüştürücüler yazmak için başvuru uygulamaları olarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1482-158">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="f1482-159">Fabrika deseninin izlenmesi için adımlar</span><span class="sxs-lookup"><span data-stu-id="f1482-159">Steps to follow the factory pattern</span></span>

<span data-ttu-id="f1482-160">Aşağıdaki adımlarda, fabrika modelini izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f1482-160">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="f1482-161">Öğesinden türetilen bir sınıf oluşturun <xref:System.Text.Json.Serialization.JsonConverterFactory> .</span><span class="sxs-lookup"><span data-stu-id="f1482-161">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="f1482-162">`CanConvert`Dönüştürülecek tür dönüştürücünün işleyebileceği bir ise true döndürecek şekilde yöntemi geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="f1482-162">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="f1482-163">Örneğin, dönüştürücü için ise `List<T>` yalnızca `List<int>` , `List<string>` ve işleyebilir `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="f1482-163">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="f1482-164">`CreateConverter`Çalışma zamanında belirtilen tür dönüşümü işleyecek bir dönüştürücü sınıfının örneğini döndürmek için yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="f1482-164">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="f1482-165">Yöntemin örnekleyen Converter sınıfını oluşturun `CreateConverter` .</span><span class="sxs-lookup"><span data-stu-id="f1482-165">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="f1482-166">Açık genel türler için fabrika deseninin olması gerekir çünkü bir nesneyi bir dizeye ve bu dizeden dönüştürecek kod tüm türler için aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="f1482-166">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="f1482-167">Açık genel tür için bir dönüştürücü ( `List<T>` Örneğin,), arka plandaki bir kapalı genel tür (örneğin) için bir dönüştürücü oluşturmaktır `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="f1482-167">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="f1482-168">Dönüştürücünün işleyebileceği her bir kapalı genel türü işlemek için kodun yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1482-168">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="f1482-169">`Enum`Tür, açık bir genel türe benzer: bir dönüştürücünün, `Enum` `Enum` arka planda belirli bir (örneğin,) bir dönüştürücü oluşturması gerekir `WeekdaysEnum` .</span><span class="sxs-lookup"><span data-stu-id="f1482-169">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="f1482-170">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="f1482-170">Error handling</span></span>

<span data-ttu-id="f1482-171">Seri hale getirici özel durum türleri ve için özel işleme sağlar <xref:System.Text.Json.JsonException> <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="f1482-171">The serializer provides special handling for exception types <xref:System.Text.Json.JsonException> and <xref:System.NotSupportedException>.</span></span>

### <a name="jsonexception"></a><span data-ttu-id="f1482-172">JsonException</span><span class="sxs-lookup"><span data-stu-id="f1482-172">JsonException</span></span>

<span data-ttu-id="f1482-173">İleti olmadan bir oluşturursanız `JsonException` , serileştirici, hataya neden olan JSON bölümünün yolunu içeren bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1482-173">If you throw a `JsonException` without a message, the serializer creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="f1482-174">Örneğin, ifade `throw new JsonException()` Aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:</span><span class="sxs-lookup"><span data-stu-id="f1482-174">For example, the statement `throw new JsonException()` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="f1482-175">Bir ileti sağlarsanız (örneğin, `throw new JsonException("Error occurred")` seri hale getirici hala <xref:System.Text.Json.JsonException.Path> , <xref:System.Text.Json.JsonException.LineNumber> ve özelliklerini ayarlarsa) <xref:System.Text.Json.JsonException.BytePositionInLine> .</span><span class="sxs-lookup"><span data-stu-id="f1482-175">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the serializer still sets the <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber>, and <xref:System.Text.Json.JsonException.BytePositionInLine> properties.</span></span>

### <a name="notsupportedexception"></a><span data-ttu-id="f1482-176">NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="f1482-176">NotSupportedException</span></span>

<span data-ttu-id="f1482-177">Bir oluşturursanız `NotSupportedException` , her zaman iletideki yol bilgilerini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f1482-177">If you throw a `NotSupportedException`, you always get the path information in the message.</span></span> <span data-ttu-id="f1482-178">Bir ileti sağlarsanız, yol bilgileri buna eklenir.</span><span class="sxs-lookup"><span data-stu-id="f1482-178">If you provide a message, the path information is appended to it.</span></span> <span data-ttu-id="f1482-179">Örneğin, ifade `throw new NotSupportedException("Error occurred.")` Aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:</span><span class="sxs-lookup"><span data-stu-id="f1482-179">For example, the statement `throw new NotSupportedException("Error occurred.")` produces an error message like the following example:</span></span>

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a><span data-ttu-id="f1482-180">Hangi özel durum türünü throw</span><span class="sxs-lookup"><span data-stu-id="f1482-180">When to throw which exception type</span></span>

<span data-ttu-id="f1482-181">JSON yükü, seri durumdan çıkarılacak tür için geçerli olmayan belirteçler içerdiğinde bir oluşturun `JsonException` .</span><span class="sxs-lookup"><span data-stu-id="f1482-181">When the JSON payload contains tokens that are not valid for the type being deserialized, throw a `JsonException`.</span></span>

<span data-ttu-id="f1482-182">Belirli türlere izin vermemek istediğinizde, oluşturun `NotSupportedException` .</span><span class="sxs-lookup"><span data-stu-id="f1482-182">When you want to disallow certain types, throw a `NotSupportedException`.</span></span> <span data-ttu-id="f1482-183">Bu özel durum, seri hale getiricinin desteklenmeyen türler için otomatik olarak ne yaptığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1482-183">This exception is what the serializer automatically throws for types that are not supported.</span></span> <span data-ttu-id="f1482-184">Örneğin, `System.Type` Güvenlik nedenleriyle desteklenmez. bu nedenle, bunun sonucunda sonuçları serisini kaldırma girişimi `NotSupportedException` .</span><span class="sxs-lookup"><span data-stu-id="f1482-184">For example, `System.Type` is not supported for security reasons, so an attempt to deserialize it results in a `NotSupportedException`.</span></span>

<span data-ttu-id="f1482-185">Gerektiğinde başka özel durumlar da oluşturabilirsiniz, ancak bunlar otomatik olarak JSON yol bilgilerini içermez.</span><span class="sxs-lookup"><span data-stu-id="f1482-185">You can throw other exceptions as needed, but they don't automatically include JSON path information.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="f1482-186">Özel dönüştürücüyü kaydetme</span><span class="sxs-lookup"><span data-stu-id="f1482-186">Register a custom converter</span></span>

<span data-ttu-id="f1482-187"> `Serialize` Ve yöntemlerinin onu kullanmasını sağlamak için özel bir dönüştürücü kaydedin `Deserialize` .</span><span class="sxs-lookup"><span data-stu-id="f1482-187">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="f1482-188">Aşağıdaki yaklaşımlardan birini seçin:</span><span class="sxs-lookup"><span data-stu-id="f1482-188">Choose one of the following approaches:</span></span>

* <span data-ttu-id="f1482-189">Koleksiyona Converter sınıfının bir örneğini ekleyin <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f1482-189">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="f1482-190">Özel dönüştürücü gerektiren özelliklere [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f1482-190">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="f1482-191">[[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini bir sınıfa veya özel bir değer türünü temsil eden bir yapıya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f1482-191">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="f1482-192">Kayıt örneği-dönüştürücüler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="f1482-192">Registration sample - Converters collection</span></span>

<span data-ttu-id="f1482-193">Aşağıda <xref:System.ComponentModel.DateTimeOffsetConverter> , türü özellikler için varsayılan değer sağlayan bir örnek verilmiştir <xref:System.DateTimeOffset> :</span><span class="sxs-lookup"><span data-stu-id="f1482-193">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

<span data-ttu-id="f1482-194">Aşağıdaki türde bir örneği serileştirdiğinizi varsayın:</span><span class="sxs-lookup"><span data-stu-id="f1482-194">Suppose you serialize an instance of the following type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="f1482-195">Özel dönüştürücünün kullanıldığını gösteren bir JSON çıkışı örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1482-195">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="f1482-196">Aşağıdaki kod özel dönüştürücüyü kullanarak seri durumdan çıkarmak için aynı yaklaşımı kullanır `DateTimeOffset` :</span><span class="sxs-lookup"><span data-stu-id="f1482-196">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="f1482-197">Kayıt örneği-[JsonConverter] bir özellikte</span><span class="sxs-lookup"><span data-stu-id="f1482-197">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="f1482-198">Aşağıdaki kod, özelliği için özel bir dönüştürücü seçer `Date` :</span><span class="sxs-lookup"><span data-stu-id="f1482-198">The following code selects a custom converter for the `Date` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

<span data-ttu-id="f1482-199">Seri hale getirilecek kod şunu kullanılmasını `WeatherForecastWithConverterAttribute` gerektirmez `JsonSerializeOptions.Converters` :</span><span class="sxs-lookup"><span data-stu-id="f1482-199">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

<span data-ttu-id="f1482-200">Seri durumdan çıkarılacak kod ayrıca kullanımını gerektirmez `Converters` :</span><span class="sxs-lookup"><span data-stu-id="f1482-200">The code to deserialize also doesn't require the use of `Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="f1482-201">Kayıt örneği-[JsonConverter] bir tür üzerinde</span><span class="sxs-lookup"><span data-stu-id="f1482-201">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="f1482-202">Bir struct oluşturan ve özniteliği uygulayan kod aşağıda verilmiştir `[JsonConverter]` :</span><span class="sxs-lookup"><span data-stu-id="f1482-202">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

<span data-ttu-id="f1482-203">Önceki yapı için özel dönüştürücü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1482-203">Here's the custom converter for the preceding struct:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

<span data-ttu-id="f1482-204">`[JsonConvert]`Yapı üzerindeki özniteliği özel dönüştürücüyü türü özellikler için varsayılan olarak kaydeder `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="f1482-204">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="f1482-205">Dönüştürücü, `TemperatureCelsius` seri hale getirmek veya serisini kaldırmak için aşağıdaki türün özelliğinde otomatik olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="f1482-205">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a><span data-ttu-id="f1482-206">Dönüştürücü kayıt önceliği</span><span class="sxs-lookup"><span data-stu-id="f1482-206">Converter registration precedence</span></span>

<span data-ttu-id="f1482-207">Serileştirme veya seri durumundan çıkarma sırasında, en yüksek öncelikten en düşüğe doğru listelenen her bir JSON öğesi için bir dönüştürücü seçilir:</span><span class="sxs-lookup"><span data-stu-id="f1482-207">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="f1482-208">`[JsonConverter]` bir özelliğe uygulandı.</span><span class="sxs-lookup"><span data-stu-id="f1482-208">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="f1482-209">Koleksiyona eklenen bir dönüştürücü `Converters` .</span><span class="sxs-lookup"><span data-stu-id="f1482-209">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="f1482-210">`[JsonConverter]` özel bir değer türüne veya POCO 'a uygulandı.</span><span class="sxs-lookup"><span data-stu-id="f1482-210">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="f1482-211">Bir tür için birden çok özel dönüştürücü `Converters` koleksiyonda kayıtlıysa, için true döndüren ilk dönüştürücü `CanConvert` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1482-211">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="f1482-212">Yalnızca uygulanabilir özel dönüştürücü kayıtlı değilse, yerleşik bir dönüştürücü seçilir.</span><span class="sxs-lookup"><span data-stu-id="f1482-212">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="f1482-213">Yaygın senaryolar için dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="f1482-213">Converter samples for common scenarios</span></span>

<span data-ttu-id="f1482-214">Aşağıdaki bölümlerde, yerleşik işlevlerin sağlamadığı bazı yaygın senaryolar ele alan dönüştürücü örnekleri sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1482-214">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="f1482-215">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f1482-215">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f1482-216">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f1482-216">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f1482-217">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f1482-217">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="f1482-218">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f1482-218">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f1482-219">[Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="f1482-219">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="f1482-220">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f1482-220">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f1482-221">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f1482-221">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="f1482-222">Çıkartılan türlerin nesne özelliklerine serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="f1482-222">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="f1482-223">Türünde bir özelliğe seri durumdan çıkarılırken `object` bir `JsonElement` nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f1482-223">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="f1482-224">Bunun nedeni, seri hale getiricinin oluşturulacak CLR türünü bilmeyeceği ve tahmin etmeye çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="f1482-224">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="f1482-225">Örneğin, bir JSON özelliğinde "true" varsa, seri hale getirici değerin bir olduğunu `Boolean` ve bir öğede "01/01/2019" varsa, seri hale getiricinin bir olduğunu çıkarmaz `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="f1482-225">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="f1482-226">Tür çıkarımı yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1482-226">Type inference can be inaccurate.</span></span> <span data-ttu-id="f1482-227">Seri hale getirici, ondalık noktası olmayan bir JSON numarasını ayrıştırır `long` . Bu, değerin başlangıçta veya olarak seri hale getirilmediği durumlarda Aralık dışı sorunlara yol açabilir `ulong` `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="f1482-227">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="f1482-228">`double`Sayı ilk olarak bir olarak seri hale getirilemediği takdirde, ondalık noktası olan bir sayının ayrıştırmasında duyarlık kaybolabilir `decimal` .</span><span class="sxs-lookup"><span data-stu-id="f1482-228">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="f1482-229">Tür çıkarımı gerektiren senaryolar için aşağıdaki kod, özellikler için özel bir dönüştürücü gösterir `object` .</span><span class="sxs-lookup"><span data-stu-id="f1482-229">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="f1482-230">Kod dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="f1482-230">The code converts:</span></span>

* <span data-ttu-id="f1482-231">`true` ve `false` için `Boolean`</span><span class="sxs-lookup"><span data-stu-id="f1482-231">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="f1482-232">Ondalık olmayan sayılar `long`</span><span class="sxs-lookup"><span data-stu-id="f1482-232">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="f1482-233">Ondalık sayı olan sayılar `double`</span><span class="sxs-lookup"><span data-stu-id="f1482-233">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="f1482-234">Tarihler `DateTime`</span><span class="sxs-lookup"><span data-stu-id="f1482-234">Dates to `DateTime`</span></span>
* <span data-ttu-id="f1482-235">Dizeler `string`</span><span class="sxs-lookup"><span data-stu-id="f1482-235">Strings to `string`</span></span>
* <span data-ttu-id="f1482-236">Diğer her şey `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="f1482-236">Everything else to `JsonElement`</span></span>

::: zone pivot="dotnet-5-0"

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterInferredTypesToObject.cs":::

<span data-ttu-id="f1482-237">Örnekte, dönüştürücü kodu ve `WeatherForecast` özellikleri olan bir sınıf gösterilmektedir `object` .</span><span class="sxs-lookup"><span data-stu-id="f1482-237">The example shows the converter code and a `WeatherForecast` class with `object` properties.</span></span> <span data-ttu-id="f1482-238">`Main`Yöntemi, `WeatherForecast` önce dönüştürücüyü kullanmadan, sonra dönüştürücüyü kullanarak bir JSON dizesini bir örneğe seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f1482-238">The `Main` method deserializes a JSON string into a `WeatherForecast` instance, first without using the converter, and then using the converter.</span></span> <span data-ttu-id="f1482-239">Konsol çıktısı, özelliği için çalışma zamanı türü olan dönüştürücü olmadan, `Date` `JsonElement` çalışma zamanı türünün olduğunu gösterir `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="f1482-239">The console output shows that without the converter the run time type for the `Date` property is `JsonElement`; with the converter, the run time type is `DateTime`.</span></span>

<span data-ttu-id="f1482-240">Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/tree/c72b54243ade2e1118ab24476220a2eba6057466/src/libraries/System.Text.Json/tests/Serialization/) , `System.Text.Json.Serialization` özellikleri seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir `object` .</span><span class="sxs-lookup"><span data-stu-id="f1482-240">The [unit tests folder](https://github.com/dotnet/runtime/tree/c72b54243ade2e1118ab24476220a2eba6057466/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

:::zone-end

::: zone pivot="dotnet-core-3-1"

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

<span data-ttu-id="f1482-241">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f1482-241">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

<span data-ttu-id="f1482-242">Özelliklere sahip örnek bir tür aşağıda verilmiştir `object` :</span><span class="sxs-lookup"><span data-stu-id="f1482-242">Here's an example type with `object` properties:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

<span data-ttu-id="f1482-243">Seri durumdan çıkarılacak aşağıdaki JSON örneği,, ve olarak seri durumdan çıkarılacak değerler `DateTime` içerir `long` `string` :</span><span class="sxs-lookup"><span data-stu-id="f1482-243">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="f1482-244">Özel dönüştürücü olmadan, seri durumdan çıkarma `JsonElement` her özelliğe bir koyar.</span><span class="sxs-lookup"><span data-stu-id="f1482-244">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="f1482-245">Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , `System.Text.Json.Serialization` özellikleri seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir `object` .</span><span class="sxs-lookup"><span data-stu-id="f1482-245">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

:::zone-end

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="f1482-246">Dize olmayan anahtarla destek sözlüğü</span><span class="sxs-lookup"><span data-stu-id="f1482-246">Support Dictionary with non-string key</span></span>

<span data-ttu-id="f1482-247">Sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>` .</span><span class="sxs-lookup"><span data-stu-id="f1482-247">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="f1482-248">Diğer bir deyişle, anahtar bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1482-248">That is, the key must be a string.</span></span> <span data-ttu-id="f1482-249">Anahtar olarak bir tamsayı veya başka tür içeren bir sözlüğü desteklemek için özel bir dönüştürücü gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1482-249">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="f1482-250">Aşağıdaki kod ile birlikte çalışarak özel bir dönüştürücüyü göstermektedir `Dictionary<Enum,TValue>` :</span><span class="sxs-lookup"><span data-stu-id="f1482-250">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="f1482-251">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f1482-251">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

<span data-ttu-id="f1482-252">Dönüştürücü, aşağıdakileri `TemperatureRanges` kullanan aşağıdaki sınıfın özelliğini seri hale getirebilirsiniz ve serisini kaldıramıyor `Enum` :</span><span class="sxs-lookup"><span data-stu-id="f1482-252">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

<span data-ttu-id="f1482-253">Seri hale getirme işleminden alınan JSON çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="f1482-253">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="f1482-254">Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , `System.Text.Json.Serialization` dize dışı anahtar sözlüklerini işleyen özel dönüştürücülere daha fazla örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="f1482-254">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="f1482-255">Polimorfik serisini destekler</span><span class="sxs-lookup"><span data-stu-id="f1482-255">Support polymorphic deserialization</span></span>

<span data-ttu-id="f1482-256">Yerleşik özellikler sınırlı sayıda [polimorfik serileştirme](system-text-json-polymorphism.md) sağlar, ancak hiçbir zaman serisini kaldırma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="f1482-256">Built-in features provide a limited range of [polymorphic serialization](system-text-json-polymorphism.md) but no support for deserialization at all.</span></span> <span data-ttu-id="f1482-257">Seri durumdan çıkarma özel bir dönüştürücü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f1482-257">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="f1482-258">Örneğin, `Person` `Employee` ve türetilmiş sınıflar içeren bir soyut taban sınıfınız olduğunu varsayalım `Customer` .</span><span class="sxs-lookup"><span data-stu-id="f1482-258">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="f1482-259">Polimorfik seri kaldırma, tasarım zamanında `Person` , seri durumdan çıkarma hedefi olarak belirtebileceğiniz ve `Customer` `Employee` JSON 'daki nesnelerin çalışma zamanında doğru bir şekilde seri durumdan çıkarılması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f1482-259">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="f1482-260">Seri durumdan çıkarma sırasında, JSON 'da gerekli türü tanımlayan ipuçları bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1482-260">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="f1482-261">Kullanılabilir ipuçları türleri her senaryoya göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1482-261">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="f1482-262">Örneğin, bir Ayrıştırıcı özelliği kullanılabilir olabilir veya belirli bir özelliğin varlığına veya yokluğuna güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1482-262">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="f1482-263">Geçerli sürümü, çok `System.Text.Json` biçimli seri kaldırma senaryolarını nasıl işleyeceğinizi belirtmek için öznitelikler sağlamaz, bu nedenle özel dönüştürücüler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1482-263">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="f1482-264">Aşağıdaki kod, temel sınıfı, iki türetilmiş sınıfı ve bunlar için özel bir dönüştürücüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1482-264">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="f1482-265">Dönüştürücü, çok biçimli seri kaldırma işlemi yapmak için bir Ayrıştırıcı özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1482-265">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="f1482-266">Tür ayrıştırıcısı sınıf tanımlarında değildir, ancak serileştirme sırasında oluşturulur ve seri durumundan çıkarma sırasında okunabilir.</span><span class="sxs-lookup"><span data-stu-id="f1482-266">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

<span data-ttu-id="f1482-267">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f1482-267">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

<span data-ttu-id="f1482-268">Dönüştürücü, serileştirme için aynı dönüştürücü kullanılarak oluşturulan JSON serisini kaldıramıyor, örneğin:</span><span class="sxs-lookup"><span data-stu-id="f1482-268">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

<span data-ttu-id="f1482-269">Yukarıdaki örnekteki dönüştürücü kodu, her bir özelliği el ile okur ve yazar.</span><span class="sxs-lookup"><span data-stu-id="f1482-269">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="f1482-270">Bir alternatif, çalışmanın bir `Deserialize` kısmını çağırmak veya yapmak için kullanılır `Serialize` .</span><span class="sxs-lookup"><span data-stu-id="f1482-270">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="f1482-271">Bir örnek için, [Bu StackOverflow gönderisini](https://stackoverflow.com/a/59744873/12509023)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="f1482-271">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="f1482-272">Yığın için gidiş dönüş desteği\<T></span><span class="sxs-lookup"><span data-stu-id="f1482-272">Support round trip for Stack\<T></span></span>

<span data-ttu-id="f1482-273">Bir JSON dizesini bir nesneye serisini çıkardıysanız <xref:System.Collections.Generic.Stack%601> ve sonra bu nesneyi serileştirmek istiyorsanız, yığının içeriği ters sıralardır.</span><span class="sxs-lookup"><span data-stu-id="f1482-273">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="f1482-274">Bu davranış, aşağıdaki türler ve arabirim için ve bunlardan türetilmiş Kullanıcı tanımlı türler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f1482-274">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="f1482-275">Yığın içinde orijinal sırayı koruyan serileştirme ve serisini desteklemek için özel bir dönüştürücü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1482-275">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="f1482-276">Aşağıdaki kod, nesnelerinden ve nesnelerden gidiş dönüşü sağlayan özel bir dönüştürücüyü gösterir `Stack<T>` :</span><span class="sxs-lookup"><span data-stu-id="f1482-276">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

<span data-ttu-id="f1482-277">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f1482-277">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a><span data-ttu-id="f1482-278">Null değerleri işleme</span><span class="sxs-lookup"><span data-stu-id="f1482-278">Handle null values</span></span>

<span data-ttu-id="f1482-279">Varsayılan olarak, seri hale getirici null değerlerini aşağıdaki şekilde işler:</span><span class="sxs-lookup"><span data-stu-id="f1482-279">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="f1482-280">Başvuru türleri ve <xref:System.Nullable%601> türleri için:</span><span class="sxs-lookup"><span data-stu-id="f1482-280">For reference types and <xref:System.Nullable%601> types:</span></span>

  * <span data-ttu-id="f1482-281">`null`Serileştirme sırasında özel Dönüştürücülerine geçmez.</span><span class="sxs-lookup"><span data-stu-id="f1482-281">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="f1482-282">`JsonTokenType.Null`Seri durumdan çıkarma sırasında özel Dönüştürücülerine geçmez.</span><span class="sxs-lookup"><span data-stu-id="f1482-282">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="f1482-283">`null`Seri durumdan çıkarma üzerine bir örnek döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1482-283">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="f1482-284">`null`Serileştirme üzerinde doğrudan yazıcıya yazar.</span><span class="sxs-lookup"><span data-stu-id="f1482-284">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="f1482-285">Null yapılamayan değer türleri için:</span><span class="sxs-lookup"><span data-stu-id="f1482-285">For non-nullable value types:</span></span>

  * <span data-ttu-id="f1482-286">`JsonTokenType.Null`Seri durumdan çıkarma sırasında özel Dönüştürücülerine geçer.</span><span class="sxs-lookup"><span data-stu-id="f1482-286">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="f1482-287">(Özel dönüştürücü yoksa, `JsonException` tür için iç dönüştürücü tarafından bir özel durum oluşturulur.)</span><span class="sxs-lookup"><span data-stu-id="f1482-287">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="f1482-288">Bu null işleme davranışı öncelikle, dönüştürücünün ek bir çağrısını atlayarak performansı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="f1482-288">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="f1482-289">Ayrıca, `null` her `Read` ve `Write` yöntemi geçersiz kılmanın başlangıcında olup olmadığını kontrol etmek için null yapılabilir türler için dönüştürücüler zorlamaktan kaçınır.</span><span class="sxs-lookup"><span data-stu-id="f1482-289">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="f1482-290">Bir özel dönüştürücünün `null` bir başvuru veya değer türü için işlemesini sağlamak için, <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi, döndürecek şekilde geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="f1482-290">To enable a custom converter to handle `null` for a reference or value type, override <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="18":::
::: zone-end

## <a name="preserve-references"></a><span data-ttu-id="f1482-291">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="f1482-291">Preserve references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="f1482-292">Varsayılan olarak, başvuru verileri yalnızca veya için yapılan her çağrı için önbelleğe alınır <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.JsonSerializer.Deserialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="f1482-292">By default, reference data is only cached for each call to <xref:System.Text.Json.JsonSerializer.Serialize%2A> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A>.</span></span> <span data-ttu-id="f1482-293">Bir çağrıdan diğerine yapılan başvuruları kalıcı hale getirmek için `Serialize` / `Deserialize` , ' <xref:System.Text.Json.Serialization.ReferenceResolver> ın çağrı sitesinde kökünü yapın `Serialize` / `Deserialize` .</span><span class="sxs-lookup"><span data-stu-id="f1482-293">To persist references from one `Serialize`/`Deserialize` call to another one, root the <xref:System.Text.Json.Serialization.ReferenceResolver> instance in the call site of `Serialize`/`Deserialize`.</span></span> <span data-ttu-id="f1482-294">Aşağıdaki kod, bu senaryo için bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="f1482-294">The following code shows an example for this scenario:</span></span>

* <span data-ttu-id="f1482-295">Tür için özel bir dönüştürücü yazarsınız `Company` .</span><span class="sxs-lookup"><span data-stu-id="f1482-295">You write a custom converter for the `Company` type.</span></span>
* <span data-ttu-id="f1482-296">Özelliği olan özelliğini el ile seri hale getirmek istemezsiniz `Supervisor` `Employee` .</span><span class="sxs-lookup"><span data-stu-id="f1482-296">You don't want to manually serialize the `Supervisor` property, which is an `Employee`.</span></span> <span data-ttu-id="f1482-297">Bunu serileştiriciye atamak istiyorsunuz ve daha önce kaydettiğiniz başvuruları korumak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f1482-297">You want to delegate that to the serializer and you also want to preserve the references that you have already saved.</span></span>

<span data-ttu-id="f1482-298">`Employee`Ve `Company` sınıfları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f1482-298">Here are the `Employee` and `Company` classes:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="EmployeeAndCompany":::

<span data-ttu-id="f1482-299">Dönüştürücü şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="f1482-299">The converter looks like this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="CompanyConverter":::

<span data-ttu-id="f1482-300">Öğesinden türetilen bir sınıf <xref:System.Text.Json.Serialization.ReferenceResolver> , başvuruları bir sözlükte depolar:</span><span class="sxs-lookup"><span data-stu-id="f1482-300">A class that derives from <xref:System.Text.Json.Serialization.ReferenceResolver> stores the references in a dictionary:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="MyReferenceResolver":::

<span data-ttu-id="f1482-301">Öğesinden türetilen bir sınıf <xref:System.Text.Json.Serialization.ReferenceHandler> , bir örneğini tutar `MyReferenceResolver` ve yalnızca gerektiğinde yeni bir örnek oluşturur (Bu örnekte adlı bir yöntemde `Reset` ):</span><span class="sxs-lookup"><span data-stu-id="f1482-301">A class that derives from <xref:System.Text.Json.Serialization.ReferenceHandler> holds an instance of `MyReferenceResolver` and creates a new instance only when needed (in a method named `Reset` in this example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="MyReferenceHandler":::

<span data-ttu-id="f1482-302">Örnek kod serileştiriciyi çağırdığında, <xref:System.Text.Json.JsonSerializerOptions> <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> özelliğinin bir örneğine ayarlandığı bir örneği kullanır `MyReferenceHandler` .</span><span class="sxs-lookup"><span data-stu-id="f1482-302">When the sample code calls the serializer, it uses a <xref:System.Text.Json.JsonSerializerOptions> instance in which the <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> property is set to an instance of `MyReferenceHandler`.</span></span> <span data-ttu-id="f1482-303">Bu kalıbı izlediğinizde, `ReferenceResolver` seri hale getirmeyi tamamladıktan sonra, sonsuza kadar büyümeye devam etmek için sözlüğü sıfırladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f1482-303">When you follow this pattern, be sure to reset the `ReferenceResolver` dictionary when you're finished serializing, to keep it from growing forever.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="CallSerializer" highlight = "4-5,12":::

<span data-ttu-id="f1482-304">Yukarıdaki örnek yalnızca serileştirme amaçlıdır, ancak seri durumundan çıkarma için benzer bir yaklaşım benimsemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1482-304">The preceding example only does serialization, but a similar approach can be adopted for deserialization.</span></span>

::: zone-end
::: zone pivot="dotnet-core-3-1"

<span data-ttu-id="f1482-305">Başvuruların nasıl korunduğu hakkında daha fazla bilgi için [bu sayfanın .net 5,0 sürümüne](system-text-json-converters-how-to.md?pivots=dotnet-5-0#preserve-references)bakın.</span><span class="sxs-lookup"><span data-stu-id="f1482-305">For information about how to preserve references, see [the .NET 5.0 version of this page](system-text-json-converters-how-to.md?pivots=dotnet-5-0#preserve-references).</span></span>

::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="f1482-306">Diğer özel dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="f1482-306">Other custom converter samples</span></span>

<span data-ttu-id="f1482-307">' [Den Newtonsoft.Json System.Text.Json geçiş](system-text-json-migrate-from-newtonsoft-how-to.md) , özel dönüştürücülerin ek örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f1482-307">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="f1482-308">Kaynak kodundaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) `System.Text.Json.Serialization` , gibi diğer özel dönüştürücü örneklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f1482-308">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="f1482-309">[Seri durumdan çıkarma sırasında null değeri 0 olarak dönüştüren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="f1482-309">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="f1482-310">[Seri durumdan çıkarma sırasında hem dize hem de sayı değerlerine izin veren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="f1482-310">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="f1482-311">[Sabit Listesi Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="f1482-311">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="f1482-312">[\<T>Dış verileri kabul eden liste Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="f1482-312">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="f1482-313">[Long [] bir sayı listesi ile birlikte çalışma](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="f1482-313">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="f1482-314">Varolan bir yerleşik dönüştürücünün davranışını değiştiren bir dönüştürücü yapmanız gerekiyorsa, varolan dönüştürücünün özelleştirme için bir başlangıç noktası olarak sunmak üzere [kaynak kodunu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1482-314">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f1482-315">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f1482-315">Additional resources</span></span>

* <span data-ttu-id="f1482-316">[Yerleşik dönüştürücüler için kaynak kodu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="f1482-316">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="f1482-317">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="f1482-317">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f1482-318">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="f1482-318">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="f1482-319">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1482-319">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="f1482-320">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f1482-320">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="f1482-321">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f1482-321">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="f1482-322">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="f1482-322">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="f1482-323">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="f1482-323">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="f1482-324">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="f1482-324">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="f1482-325">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="f1482-325">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="f1482-326">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="f1482-326">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="f1482-327">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="f1482-327">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="f1482-328">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f1482-328">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f1482-329">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f1482-329">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="f1482-330">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="f1482-330">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="f1482-331">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="f1482-331">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="f1482-332">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f1482-332">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f1482-333">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f1482-333">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
