---
title: JSON serileştirme-.NET için özel dönüştürücüler yazma
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 0f8b89ec7d7b1677de085631958b888e154aa4fa
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116715"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="60582-102">.NET 'teki JSON serileştirme (sıralama) için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="60582-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="60582-103">Bu makalede, <xref:System.Text.Json> ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="60582-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="60582-104">`System.Text.Json`giriş için bkz. [.net 'TE JSON serileştirme ve seri durumdan çıkarma](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="60582-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="60582-105">*Dönüştürücü* bir nesneyi veya BIR değeri JSON öğesine veya bir değere dönüştüren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="60582-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="60582-106">`System.Text.Json` ad alanı, JavaScript temel elemanlarına eşleyen en basit türler için yerleşik dönüştürücülerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="60582-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="60582-107">Özel dönüştürücüler yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60582-107">You can write custom converters:</span></span>

* <span data-ttu-id="60582-108">Yerleşik dönüştürücünün varsayılan davranışını geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="60582-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="60582-109">Örneğin, `DateTime` değerlerinin varsayılan ISO 8601-1:2019 biçimi yerine aa/gg/yyyy biçiminde temsil olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60582-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="60582-110">Özel bir değer türünü desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="60582-110">To support a custom value type.</span></span> <span data-ttu-id="60582-111">Örneğin, bir `PhoneNumber` yapısı.</span><span class="sxs-lookup"><span data-stu-id="60582-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="60582-112">Ayrıca, geçerli sürüme dahil olmayan işlevlerle `System.Text.Json` özelleştirmek veya genişletmek için özel dönüştürücüler de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60582-112">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="60582-113">Bu makalenin ilerleyen bölümlerinde aşağıdaki senaryolar ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="60582-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="60582-114">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="60582-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="60582-115">[Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="60582-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="60582-116">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="60582-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="60582-117">Özel dönüştürücü desenleri</span><span class="sxs-lookup"><span data-stu-id="60582-117">Custom converter patterns</span></span>

<span data-ttu-id="60582-118">Özel dönüştürücü oluşturmak için iki desen vardır: temel desen ve fabrika düzeni.</span><span class="sxs-lookup"><span data-stu-id="60582-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="60582-119">Fabrika deseninin türü `Enum` işleyen veya genel türleri açık olan dönüştürücüler içindir.</span><span class="sxs-lookup"><span data-stu-id="60582-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="60582-120">Temel model, genel olmayan ve kapalı genel türler içindir.</span><span class="sxs-lookup"><span data-stu-id="60582-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="60582-121">Örneğin, aşağıdaki türler için dönüştürücüler fabrika deseninin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="60582-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="60582-122">Temel model tarafından işlenebilen türlerin bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="60582-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="60582-123">Temel model, bir türü işleyebileceğini bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60582-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="60582-124">Factory stili, çalışma zamanında belirli bir türün gerekli olduğunu ve uygun dönüştürücüyü dinamik olarak oluşturduğunu belirleyen bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60582-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="60582-125">Örnek temel dönüştürücü</span><span class="sxs-lookup"><span data-stu-id="60582-125">Sample basic converter</span></span>

<span data-ttu-id="60582-126">Aşağıdaki örnek, varolan bir veri türü için varsayılan Serileştirmeyi geçersiz kılan bir dönüştürücütür.</span><span class="sxs-lookup"><span data-stu-id="60582-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="60582-127">Dönüştürücü `DateTimeOffset` özellikleri için aa/gg/yyyy biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="60582-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="60582-128">Örnek fabrika deseninin Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="60582-128">Sample factory pattern converter</span></span>

<span data-ttu-id="60582-129">Aşağıdaki kod, `Dictionary<Enum,TValue>`ile birlikte çalışarak özel bir dönüştürücüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="60582-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="60582-130">İlk genel tür parametresi `Enum` ve ikincisi açık olduğundan, kod fabrika düzeniyle uyar.</span><span class="sxs-lookup"><span data-stu-id="60582-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="60582-131">`CanConvert` yöntemi, yalnızca bir `Enum` türü olan iki genel parametre içeren bir `Dictionary` için `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="60582-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="60582-132">İç dönüştürücü, `TValue`çalışma zamanında hangi türün sağlandığını işlemek için mevcut bir dönüştürücüyü alır.</span><span class="sxs-lookup"><span data-stu-id="60582-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="60582-133">Yukarıdaki kod, bu makalede daha sonra [dize olmayan anahtarla destek sözlüğünde](#support-dictionary-with-non-string-key) gösterilenle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="60582-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="60582-134">Temel kalıbı izlemeye yönelik adımlar</span><span class="sxs-lookup"><span data-stu-id="60582-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="60582-135">Aşağıdaki adımlarda, temel kalıbı izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="60582-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="60582-136">Seri hale getirilecek ve seri durumdan çıkarılacak tür `T` <xref:System.Text.Json.Serialization.JsonConverter%601> türetilen bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="60582-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="60582-137">Gelen JSON serisini kaldırmak için `Read` yöntemini geçersiz kılın ve `T`türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="60582-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="60582-138">JSON 'ı okumak için yöntemine geçirilen <xref:System.Text.Json.Utf8JsonReader> kullanın.</span><span class="sxs-lookup"><span data-stu-id="60582-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="60582-139">`T`türündeki gelen nesneyi seri hale getirmek için `Write` yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="60582-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="60582-140">JSON yazmak için yöntemine geçirilen <xref:System.Text.Json.Utf8JsonWriter> kullanın.</span><span class="sxs-lookup"><span data-stu-id="60582-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="60582-141">`CanConvert` yöntemini yalnızca gerekirse geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="60582-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="60582-142">Varsayılan uygulama, dönüştürülecek tür `T`türünde olduğunda `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="60582-142">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="60582-143">Bu nedenle, yalnızca tür `T` destekleyen dönüştürücüler Bu yöntemi geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60582-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="60582-144">Bu yöntemi geçersiz kılmanın gerekli olduğu dönüştürücünün bir örneği için, bu makalenin ilerleyen kısımlarında yer alan [polimorfik serisini kaldırma](#support-polymorphic-deserialization) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="60582-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="60582-145">[Yerleşik dönüştürücüler kaynak koduna](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) , özel dönüştürücüler yazmak için başvuru uygulamaları olarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60582-145">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="60582-146">Fabrika deseninin izlenmesi için adımlar</span><span class="sxs-lookup"><span data-stu-id="60582-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="60582-147">Aşağıdaki adımlarda, fabrika modelini izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="60582-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="60582-148"><xref:System.Text.Json.Serialization.JsonConverterFactory>türeten bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="60582-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="60582-149">Dönüştürülecek tür dönüştürücünün işleyebileceği bir ise true döndürecek şekilde `CanConvert` yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="60582-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="60582-150">Örneğin, dönüştürücü `List<T>` için ise yalnızca `List<int>`, `List<string>`ve `List<DateTime>`işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="60582-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="60582-151">Çalışma zamanında belirtilen tür dönüşümü işleyecek bir dönüştürücü sınıfının örneğini döndürmek için `CreateConverter` yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="60582-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="60582-152">`CreateConverter` yönteminin örnekleyen Converter sınıfını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="60582-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="60582-153">Açık genel türler için fabrika deseninin olması gerekir çünkü bir nesneyi bir dizeye ve bu dizeden dönüştürecek kod tüm türler için aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="60582-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="60582-154">Açık genel bir tür (örneğin`List<T>`) için bir dönüştürücü, arka planda kapalı bir genel tür (örneğin`List<DateTime>`) için bir dönüştürücü oluşturmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="60582-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="60582-155">Dönüştürücünün işleyebileceği her bir kapalı genel türü işlemek için kodun yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60582-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="60582-156">`Enum` türü açık bir genel türe benzer: bir `Enum` dönüştürücünün arka planda belirli bir `Enum` (örneğin,`WeekdaysEnum`) için bir dönüştürücü oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60582-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="60582-157">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="60582-157">Error handling</span></span>

<span data-ttu-id="60582-158">Hata işleme kodunda bir özel durum oluşturmanız gerekiyorsa, ileti olmadan bir <xref:System.Text.Json.JsonException> yerleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="60582-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="60582-159">Bu özel durum türü otomatik olarak, hataya neden olan JSON bölümünün yolunu içeren bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60582-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="60582-160">Örneğin, `throw new JsonException();`, aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:</span><span class="sxs-lookup"><span data-stu-id="60582-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="60582-161">Bir ileti sağlarsanız (örneğin, `throw new JsonException("Error occurred")`, özel durum yine de <xref:System.Text.Json.JsonException.Path> özelliğinde yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="60582-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="60582-162">Özel dönüştürücüyü kaydetme</span><span class="sxs-lookup"><span data-stu-id="60582-162">Register a custom converter</span></span>

<span data-ttu-id="60582-163">`Serialize` ve `Deserialize` yöntemlerinin onu kullanmasını sağlamak için özel bir dönüştürücü *kaydedin* .</span><span class="sxs-lookup"><span data-stu-id="60582-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="60582-164">Aşağıdaki yaklaşımlardan birini seçin:</span><span class="sxs-lookup"><span data-stu-id="60582-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="60582-165">Dönüştürücü sınıfının bir örneğini <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60582-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="60582-166">Özel dönüştürücü gerektiren özelliklere [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="60582-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="60582-167">[[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini bir sınıfa veya özel bir değer türünü temsil eden bir yapıya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="60582-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="60582-168">Kayıt örneği-dönüştürücüler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="60582-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="60582-169">Aşağıda, <xref:System.DateTimeOffset>türü özellikler için <xref:System.ComponentModel.DateTimeOffsetConverter> varsayılan değer veren bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60582-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="60582-170">Aşağıdaki türde bir örneği serileştirdiğinizi varsayın:</span><span class="sxs-lookup"><span data-stu-id="60582-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="60582-171">Özel dönüştürücünün kullanıldığını gösteren bir JSON çıkışı örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60582-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="60582-172">Aşağıdaki kod, özel `DateTimeOffset` dönüştürücüsünü kullanarak seri durumdan çıkarmak için aynı yaklaşımı kullanır:</span><span class="sxs-lookup"><span data-stu-id="60582-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="60582-173">Kayıt örneği-[JsonConverter] bir özellikte</span><span class="sxs-lookup"><span data-stu-id="60582-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="60582-174">Aşağıdaki kod `Date` özelliği için özel bir dönüştürücü seçer:</span><span class="sxs-lookup"><span data-stu-id="60582-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="60582-175">`WeatherForecastWithConverterAttribute` seri hale getirilecek kod `JsonSerializeOptions.Converters`kullanımını gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="60582-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="60582-176">Seri durumdan çıkarılacak kod ayrıca `Converters`kullanımını gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="60582-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="60582-177">Kayıt örneği-[JsonConverter] bir tür üzerinde</span><span class="sxs-lookup"><span data-stu-id="60582-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="60582-178">Bir struct oluşturan ve `[JsonConverter]` özniteliğini uygulayan kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60582-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="60582-179">Önceki yapı için özel dönüştürücü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60582-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="60582-180">Yapı üzerindeki `[JsonConvert]` özniteliği, özel dönüştürücüyü `Temperature`türü özellikler için varsayılan olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="60582-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="60582-181">Dönüştürücü, seri hale getirmek veya serisini kaldırmak için aşağıdaki türün `TemperatureCelsius` özelliğinde otomatik olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="60582-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="60582-182">Dönüştürücü kayıt önceliği</span><span class="sxs-lookup"><span data-stu-id="60582-182">Converter registration precedence</span></span>

<span data-ttu-id="60582-183">Serileştirme veya seri durumundan çıkarma sırasında, en yüksek öncelikten en düşüğe doğru listelenen her bir JSON öğesi için bir dönüştürücü seçilir:</span><span class="sxs-lookup"><span data-stu-id="60582-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="60582-184">bir özelliğe uygulandı `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="60582-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="60582-185">`Converters` koleksiyonuna bir dönüştürücü eklendi.</span><span class="sxs-lookup"><span data-stu-id="60582-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="60582-186">özel bir değer türüne veya POCO 'a uygulanan `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="60582-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="60582-187">Bir tür için birden çok özel dönüştürücü `Converters` koleksiyonuna kayıtlıysa, `CanConvert` için true döndüren ilk dönüştürücü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60582-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="60582-188">Yalnızca uygulanabilir özel dönüştürücü kayıtlı değilse, yerleşik bir dönüştürücü seçilir.</span><span class="sxs-lookup"><span data-stu-id="60582-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="60582-189">Yaygın senaryolar için dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="60582-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="60582-190">Aşağıdaki bölümlerde, yerleşik işlevlerin sağlamadığı bazı yaygın senaryolar ele alan dönüştürücü örnekleri sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60582-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="60582-191">Çıkartılan türlerin nesne özelliklerine serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="60582-191">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="60582-192">Dize olmayan anahtarla destek sözlüğü</span><span class="sxs-lookup"><span data-stu-id="60582-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="60582-193">Polimorfik serisini destekler</span><span class="sxs-lookup"><span data-stu-id="60582-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="60582-194">Çıkartılan türlerin nesne özelliklerine serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="60582-194">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="60582-195">`object`türünde bir özelliğin serisi kaldırılırken, bir `JsonElement` nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="60582-195">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="60582-196">Bunun nedeni, seri hale getiricinin oluşturulacak CLR türünü bilmeyeceği ve tahmin etmeye çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="60582-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="60582-197">Örneğin, bir JSON özelliğinde "true" varsa, seri hale getirici değerin bir `Boolean`olduğunu ve bir öğede "01/01/2019" varsa, seri hale getirici bir `DateTime`olduğunu çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="60582-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="60582-198">Tür çıkarımı yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="60582-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="60582-199">Seri hale getirici, `long`olarak ondalık noktası olmayan bir JSON numarası ayrıştırdığında, bu, değerin başlangıçta bir `ulong` veya `BigInteger`olarak serileştirildiği, Aralık dışı sorunlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="60582-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="60582-200">Sayı ilk olarak bir `decimal`olarak seri hale getirileolduysa, `double` ondalık noktası olan bir sayının çözümlenmesi duyarlık kaybedebilir.</span><span class="sxs-lookup"><span data-stu-id="60582-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="60582-201">Tür çıkarımı gerektiren senaryolar için aşağıdaki kodda `object` özellikleri için özel bir dönüştürücü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="60582-201">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="60582-202">Kod dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="60582-202">The code converts:</span></span>

* <span data-ttu-id="60582-203">`Boolean` `true` ve `false`</span><span class="sxs-lookup"><span data-stu-id="60582-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="60582-204">`long` ondalık olmayan sayılar</span><span class="sxs-lookup"><span data-stu-id="60582-204">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="60582-205">`double` ondalık sayı olan sayılar</span><span class="sxs-lookup"><span data-stu-id="60582-205">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="60582-206">`DateTime` tarihler</span><span class="sxs-lookup"><span data-stu-id="60582-206">Dates to `DateTime`</span></span>
* <span data-ttu-id="60582-207">`string` dizeler</span><span class="sxs-lookup"><span data-stu-id="60582-207">Strings to `string`</span></span>
* <span data-ttu-id="60582-208">`JsonElement` diğer her şey</span><span class="sxs-lookup"><span data-stu-id="60582-208">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="60582-209">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="60582-209">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="60582-210">Aşağıda `object` özelliklere sahip örnek bir tür verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60582-210">Here's an example type with `object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="60582-211">Seri durumdan çıkarılacak aşağıdaki JSON örneği, `DateTime`, `long`ve `string`olarak seri durumdan çıkarılacak değerler içerir:</span><span class="sxs-lookup"><span data-stu-id="60582-211">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="60582-212">Özel dönüştürücü olmadan, seri durumdan çıkarma her özelliğe bir `JsonElement` koyar.</span><span class="sxs-lookup"><span data-stu-id="60582-212">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="60582-213">`System.Text.Json.Serialization` ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , `object` özelliklerini seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="60582-213">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="60582-214">Dize olmayan anahtarla destek sözlüğü</span><span class="sxs-lookup"><span data-stu-id="60582-214">Support Dictionary with non-string key</span></span>

<span data-ttu-id="60582-215">Sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>`içindir.</span><span class="sxs-lookup"><span data-stu-id="60582-215">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="60582-216">Diğer bir deyişle, anahtar bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60582-216">That is, the key must be a string.</span></span> <span data-ttu-id="60582-217">Anahtar olarak bir tamsayı veya başka tür içeren bir sözlüğü desteklemek için özel bir dönüştürücü gerekir.</span><span class="sxs-lookup"><span data-stu-id="60582-217">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="60582-218">Aşağıdaki kod, `Dictionary<Enum,TValue>`ile birlikte çalışarak özel bir dönüştürücüyü gösterir:</span><span class="sxs-lookup"><span data-stu-id="60582-218">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="60582-219">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="60582-219">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="60582-220">Dönüştürücü aşağıdaki `Enum`kullanan aşağıdaki sınıfın `TemperatureRanges` özelliğini seri hale getirebilirsiniz ve serisini kaldıramıyor:</span><span class="sxs-lookup"><span data-stu-id="60582-220">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="60582-221">Seri hale getirme işleminden alınan JSON çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="60582-221">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="60582-222">`System.Text.Json.Serialization` ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , dize dışı anahtar sözlüklerini işleyen özel dönüştürücülere daha fazla örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="60582-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="60582-223">Polimorfik serisini destekler</span><span class="sxs-lookup"><span data-stu-id="60582-223">Support polymorphic deserialization</span></span>

<span data-ttu-id="60582-224">Yerleşik özellikler sınırlı sayıda [polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) sağlar, ancak hiçbir zaman serisini kaldırma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="60582-224">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="60582-225">Seri durumdan çıkarma özel bir dönüştürücü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="60582-225">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="60582-226">Örneğin, `Employee` ve `Customer` türetilmiş sınıflarla `Person` soyut bir temel sınıfınız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="60582-226">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="60582-227">Polimorfik seri kaldırma, tasarım zamanında `Person` serisini kaldırma hedefi olarak belirtebileceğiniz ve `Customer` ve JSON 'daki `Employee` nesnelerinin çalışma zamanında doğru şekilde seri durumdan çıkarılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="60582-227">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="60582-228">Seri durumdan çıkarma sırasında, JSON 'da gerekli türü tanımlayan ipuçları bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60582-228">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="60582-229">Kullanılabilir ipuçları türleri her senaryoya göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="60582-229">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="60582-230">Örneğin, bir Ayrıştırıcı özelliği kullanılabilir olabilir veya belirli bir özelliğin varlığına veya yokluğuna güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60582-230">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="60582-231">`System.Text.Json` geçerli sürümü, çok biçimli seri kaldırma senaryolarının nasıl işleneceğini belirtmek için öznitelikler sağlamaz, bu nedenle özel dönüştürücüler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60582-231">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="60582-232">Aşağıdaki kod, temel sınıfı, iki türetilmiş sınıfı ve bunlar için özel bir dönüştürücüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="60582-232">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="60582-233">Dönüştürücü, çok biçimli seri kaldırma işlemi yapmak için bir Ayrıştırıcı özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="60582-233">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="60582-234">Tür ayrıştırıcısı sınıf tanımlarında değildir, ancak serileştirme sırasında oluşturulur ve seri durumundan çıkarma sırasında okunabilir.</span><span class="sxs-lookup"><span data-stu-id="60582-234">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="60582-235">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="60582-235">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="60582-236">Dönüştürücü, serileştirme için aynı dönüştürücü kullanılarak oluşturulan JSON serisini kaldıramıyor, örneğin:</span><span class="sxs-lookup"><span data-stu-id="60582-236">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="60582-237">Yukarıdaki örnekteki dönüştürücü kodu, her bir özelliği el ile okur ve yazar.</span><span class="sxs-lookup"><span data-stu-id="60582-237">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="60582-238">Diğer bir seçenek de `Deserialize` veya `Serialize` çağrı yapmak için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="60582-238">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="60582-239">Bir örnek için, [Bu StackOverflow gönderisini](https://stackoverflow.com/a/59744873/12509023)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="60582-239">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

## <a name="other-custom-converter-samples"></a><span data-ttu-id="60582-240">Diğer özel dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="60582-240">Other custom converter samples</span></span>

<span data-ttu-id="60582-241">[Newtonsoft. JSON 'Dan System. Text. JSON 'A geçiş](system-text-json-migrate-from-newtonsoft-how-to.md) , özel dönüştürücülerin ek örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="60582-241">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="60582-242">`System.Text.Json.Serialization` kaynak kodundaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , aşağıdakiler gibi diğer özel dönüştürücü örneklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="60582-242">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* [<span data-ttu-id="60582-243">Seri durumdan çıkarma sırasında null değeri 0 olarak dönüştüren Int32 Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="60582-243">Int32 converter that converts null to 0 on deserialize</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [<span data-ttu-id="60582-244">Seri durumdan çıkarma sırasında hem dize hem de sayı değerlerine izin veren Int32 Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="60582-244">Int32 converter that allows both string and number values on deserialize</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [<span data-ttu-id="60582-245">Sabit Listesi Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="60582-245">Enum converter</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [<span data-ttu-id="60582-246">Dış verileri kabul eden\<T > dönüştürücüsünü listeleyin</span><span class="sxs-lookup"><span data-stu-id="60582-246">List\<T> converter that accepts external data</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* <span data-ttu-id="60582-247">[Long [] bir sayı listesi ile birlikte çalışma](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="60582-247">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span> 

<span data-ttu-id="60582-248">Varolan bir yerleşik dönüştürücünün davranışını değiştiren bir dönüştürücü yapmanız gerekiyorsa, varolan dönüştürücünün özelleştirme için bir başlangıç noktası olarak sunmak üzere [kaynak kodunu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60582-248">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="60582-249">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="60582-249">Additional resources</span></span>

* [<span data-ttu-id="60582-250">Yerleşik dönüştürücüler için kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="60582-250">Source code for built-in converters</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [<span data-ttu-id="60582-251">System. Text. JSON içinde DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="60582-251">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="60582-252">System. Text. JSON genel bakış</span><span class="sxs-lookup"><span data-stu-id="60582-252">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="60582-253">System. Text. JSON kullanma</span><span class="sxs-lookup"><span data-stu-id="60582-253">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="60582-254">Newtonsoft. JSON 'dan geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="60582-254">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="60582-255">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="60582-255">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="60582-256">System. Text. JSON. Serialization API başvurusu</span><span class="sxs-lookup"><span data-stu-id="60582-256">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
