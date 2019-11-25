---
title: JSON serileştirme-.NET için özel dönüştürücüler yazma
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 33d1cd7764e71d9e2fa382c9f3c5feb77e8defb4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283343"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="9f2ff-102">.NET 'teki JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="9f2ff-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="9f2ff-103">Bu makalede, <xref:System.Text.Json> ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="9f2ff-104">`System.Text.Json`giriş için bkz. [.net 'TE JSON serileştirme ve seri durumdan çıkarma](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="9f2ff-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="9f2ff-105">*Dönüştürücü* bir nesneyi veya BIR değeri JSON öğesine veya bir değere dönüştüren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="9f2ff-106">`System.Text.Json` ad alanı, JavaScript temel elemanlarına eşleyen en basit türler için yerleşik dönüştürücülerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="9f2ff-107">Özel dönüştürücüler yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-107">You can write custom converters:</span></span>

* <span data-ttu-id="9f2ff-108">Yerleşik dönüştürücünün varsayılan davranışını geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="9f2ff-109">Örneğin, `DateTime` değerlerinin varsayılan ISO 8601-1:2019 biçimi yerine aa/gg/yyyy biçiminde temsil olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="9f2ff-110">Özel bir değer türünü desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-110">To support a custom value type.</span></span> <span data-ttu-id="9f2ff-111">Örneğin, bir `PhoneNumber` yapısı.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="9f2ff-112">Ayrıca, geçerli sürüme dahil olmayan işlevlerle `System.Text.Json` genişletmek için özel dönüştürücüler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="9f2ff-113">Bu makalenin ilerleyen bölümlerinde aşağıdaki senaryolar ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="9f2ff-114">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="9f2ff-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="9f2ff-115">[Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="9f2ff-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="9f2ff-116">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="9f2ff-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="9f2ff-117">Özel dönüştürücü desenleri</span><span class="sxs-lookup"><span data-stu-id="9f2ff-117">Custom converter patterns</span></span>

<span data-ttu-id="9f2ff-118">Özel dönüştürücü oluşturmak için iki desen vardır: temel desen ve fabrika düzeni.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="9f2ff-119">Fabrika deseninin türü `Enum` işleyen veya genel türleri açık olan dönüştürücüler içindir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="9f2ff-120">Temel model, genel olmayan ve kapalı genel türler içindir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="9f2ff-121">Örneğin, aşağıdaki türler için dönüştürücüler fabrika deseninin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="9f2ff-122">Temel model tarafından işlenebilen türlerin bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="9f2ff-123">Temel model, bir türü işleyebileceğini bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="9f2ff-124">Factory stili, çalışma zamanında belirli bir türün gerekli olduğunu ve uygun dönüştürücüyü dinamik olarak oluşturduğunu belirleyen bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="9f2ff-125">Örnek temel dönüştürücü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-125">Sample basic converter</span></span>

<span data-ttu-id="9f2ff-126">Aşağıdaki örnek, varolan bir veri türü için varsayılan Serileştirmeyi geçersiz kılan bir dönüştürücütür.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="9f2ff-127">Dönüştürücü `DateTimeOffset` özellikleri için aa/gg/yyyy biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="9f2ff-128">Örnek fabrika deseninin Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-128">Sample factory pattern converter</span></span>

<span data-ttu-id="9f2ff-129">Aşağıdaki kod, `Dictionary<Enum,TValue>`ile birlikte çalışarak özel bir dönüştürücüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="9f2ff-130">İlk genel tür parametresi `Enum` ve ikincisi açık olduğundan, kod fabrika düzeniyle uyar.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="9f2ff-131">`CanConvert` yöntemi, yalnızca bir `Enum` türü olan iki genel parametre içeren bir `Dictionary` için `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="9f2ff-132">İç dönüştürücü, `TValue`çalışma zamanında hangi türün sağlandığını işlemek için mevcut bir dönüştürücüyü alır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="9f2ff-133">Yukarıdaki kod, bu makalede daha sonra [dize olmayan anahtarla destek sözlüğünde](#support-dictionary-with-non-string-key) gösterilenle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="9f2ff-134">Temel kalıbı izlemeye yönelik adımlar</span><span class="sxs-lookup"><span data-stu-id="9f2ff-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="9f2ff-135">Aşağıdaki adımlarda, temel kalıbı izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="9f2ff-136">Seri hale getirilecek ve seri durumdan çıkarılacak tür `T` <xref:System.Text.Json.Serialization.JsonConverter%601> türetilen bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="9f2ff-137">Gelen JSON serisini kaldırmak için `Read` yöntemini geçersiz kılın ve `T`türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="9f2ff-138">JSON 'ı okumak için yöntemine geçirilen <xref:System.Text.Json.Utf8JsonReader> kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="9f2ff-139">`T`türündeki gelen nesneyi seri hale getirmek için `Write` yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="9f2ff-140">JSON yazmak için yöntemine geçirilen <xref:System.Text.Json.Utf8JsonWriter> kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="9f2ff-141">`CanConvert` yöntemini yalnızca gerekirse geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="9f2ff-142">Varsayılan uygulama, dönüştürülecek tür `T`tür olduğunda `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="9f2ff-143">Bu nedenle, yalnızca tür `T` destekleyen dönüştürücüler Bu yöntemi geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="9f2ff-144">Bu yöntemi geçersiz kılmanın gerekli olduğu dönüştürücünün bir örneği için, bu makalenin ilerleyen kısımlarında yer alan [polimorfik serisini kaldırma](#support-polymorphic-deserialization) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="9f2ff-145">[Yerleşik dönüştürücüler kaynak koduna](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) , özel dönüştürücüler yazmak için başvuru uygulamaları olarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="9f2ff-146">Fabrika deseninin izlenmesi için adımlar</span><span class="sxs-lookup"><span data-stu-id="9f2ff-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="9f2ff-147">Aşağıdaki adımlarda, fabrika modelini izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="9f2ff-148"><xref:System.Text.Json.Serialization.JsonConverterFactory>türeten bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="9f2ff-149">Dönüştürülecek tür dönüştürücünün işleyebileceği bir ise true döndürecek şekilde `CanConvert` yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="9f2ff-150">Örneğin, dönüştürücü `List<T>` için ise yalnızca `List<int>`, `List<string>`ve `List<DateTime>`işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="9f2ff-151">Çalışma zamanında belirtilen tür dönüşümü işleyecek bir dönüştürücü sınıfının örneğini döndürmek için `CreateConverter` yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="9f2ff-152">`CreateConverter` yönteminin örnekleyen Converter sınıfını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="9f2ff-153">Açık genel türler için fabrika deseninin olması gerekir çünkü bir nesneyi bir dizeye ve bu dizeden dönüştürecek kod tüm türler için aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="9f2ff-154">Açık genel bir tür (örneğin`List<T>`) için bir dönüştürücü, arka planda kapalı bir genel tür (örneğin`List<DateTime>`) için bir dönüştürücü oluşturmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="9f2ff-155">Dönüştürücünün işleyebileceği her bir kapalı genel türü işlemek için kodun yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="9f2ff-156">`Enum` türü açık bir genel türe benzer: bir `Enum` dönüştürücünün arka planda belirli bir `Enum` (örneğin,`WeekdaysEnum`) için bir dönüştürücü oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="9f2ff-157">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="9f2ff-157">Error handling</span></span>

<span data-ttu-id="9f2ff-158">Hata işleme kodunda bir özel durum oluşturmanız gerekiyorsa, ileti olmadan bir <xref:System.Text.Json.JsonException> yerleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="9f2ff-159">Bu özel durum türü otomatik olarak, hataya neden olan JSON bölümünün yolunu içeren bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="9f2ff-160">Örneğin, `throw new JsonException();`, aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="9f2ff-161">Bir ileti sağlarsanız (örneğin, `throw new JsonException("Error occurred")`, özel durum yine de <xref:System.Text.Json.JsonException.Path> özelliğinde yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="9f2ff-162">Özel dönüştürücüyü kaydetme</span><span class="sxs-lookup"><span data-stu-id="9f2ff-162">Register a custom converter</span></span>

<span data-ttu-id="9f2ff-163">`Serialize` ve `Deserialize` yöntemlerinin onu kullanmasını sağlamak için özel bir dönüştürücü *kaydedin* .</span><span class="sxs-lookup"><span data-stu-id="9f2ff-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="9f2ff-164">Aşağıdaki yaklaşımlardan birini seçin:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="9f2ff-165">Dönüştürücü sınıfının bir örneğini <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="9f2ff-166">Özel dönüştürücü gerektiren özelliklere [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="9f2ff-167">[[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini bir sınıfa veya özel bir değer türünü temsil eden bir yapıya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="9f2ff-168">Kayıt örneği-dönüştürücüler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="9f2ff-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="9f2ff-169">Aşağıda, <xref:System.DateTimeOffset>türü özellikler için <xref:System.ComponentModel.DateTimeOffsetConverter> varsayılan değer veren bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="9f2ff-170">Aşağıdaki türde bir örneği serileştirdiğinizi varsayın:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="9f2ff-171">Özel dönüştürücünün kullanıldığını gösteren bir JSON çıkışı örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="9f2ff-172">Aşağıdaki kod, özel `DateTimeOffset` dönüştürücüsünü kullanarak seri durumdan çıkarmak için aynı yaklaşımı kullanır:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="9f2ff-173">Kayıt örneği-[JsonConverter] bir özellikte</span><span class="sxs-lookup"><span data-stu-id="9f2ff-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="9f2ff-174">Aşağıdaki kod `Date` özelliği için özel bir dönüştürücü seçer:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="9f2ff-175">`WeatherForecastWithConverterAttribute` seri hale getirilecek kod `JsonSerializeOptions.Converters`kullanımını gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="9f2ff-176">Seri durumdan çıkarılacak kod ayrıca `Converters`kullanımını gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="9f2ff-177">Kayıt örneği-[JsonConverter] bir tür üzerinde</span><span class="sxs-lookup"><span data-stu-id="9f2ff-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="9f2ff-178">Bir struct oluşturan ve `[JsonConverter]` özniteliğini uygulayan kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="9f2ff-179">Önceki yapı için özel dönüştürücü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="9f2ff-180">Yapı üzerindeki `[JsonConvert]` özniteliği, özel dönüştürücüyü `Temperature`türü özellikler için varsayılan olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="9f2ff-181">Dönüştürücü, seri hale getirmek veya serisini kaldırmak için aşağıdaki türün `TemperatureCelsius` özelliğinde otomatik olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="9f2ff-182">Dönüştürücü kayıt önceliği</span><span class="sxs-lookup"><span data-stu-id="9f2ff-182">Converter registration precedence</span></span>

<span data-ttu-id="9f2ff-183">Serileştirme veya seri durumundan çıkarma sırasında, en yüksek öncelikten en düşüğe doğru listelenen her bir JSON öğesi için bir dönüştürücü seçilir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="9f2ff-184">bir özelliğe uygulandı `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="9f2ff-185">`Converters` koleksiyonuna bir dönüştürücü eklendi.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="9f2ff-186">özel bir değer türüne veya POCO 'a uygulanan `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="9f2ff-187">Bir tür için birden çok özel dönüştürücü `Converters` koleksiyonuna kayıtlıysa, `CanConvert` için true döndüren ilk dönüştürücü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="9f2ff-188">Yalnızca uygulanabilir özel dönüştürücü kayıtlı değilse, yerleşik bir dönüştürücü seçilir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="9f2ff-189">Yaygın senaryolar için dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="9f2ff-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="9f2ff-190">Aşağıdaki bölümlerde, yerleşik işlevlerin sağlamadığı bazı yaygın senaryolar ele alan dönüştürücü örnekleri sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="9f2ff-191">Çıkartılan türlerin nesne özelliklerine serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="9f2ff-191">Deserialize inferred types to Object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="9f2ff-192">Dize olmayan anahtarla destek sözlüğü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="9f2ff-193">Polimorfik serisini destekler</span><span class="sxs-lookup"><span data-stu-id="9f2ff-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="9f2ff-194">Çıkartılan türlerin nesne özelliklerine serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="9f2ff-194">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="9f2ff-195">`Object`türünde bir özelliğin serisi kaldırılırken, bir `JsonElement` nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-195">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="9f2ff-196">Bunun nedeni, seri hale getiricinin oluşturulacak CLR türünü bilmeyeceği ve tahmin etmeye çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="9f2ff-197">Örneğin, bir JSON özelliğinde "true" varsa, seri hale getirici değerin bir `Boolean`olduğunu ve bir öğede "01/01/2019" varsa, seri hale getirici bir `DateTime`olduğunu çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="9f2ff-198">Tür çıkarımı yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="9f2ff-199">Seri hale getirici, `long`olarak ondalık noktası olmayan bir JSON numarası ayrıştırdığında, bu, değerin başlangıçta bir `ulong` veya `BigInteger`olarak serileştirildiği, Aralık dışı sorunlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="9f2ff-200">Sayı ilk olarak bir `decimal`olarak seri hale getirileolduysa, `double` ondalık noktası olan bir sayının çözümlenmesi duyarlık kaybedebilir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="9f2ff-201">Tür çıkarımı gerektiren senaryolar için aşağıdaki kodda `Object` özellikleri için özel bir dönüştürücü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-201">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="9f2ff-202">Kod dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-202">The code converts:</span></span>

* <span data-ttu-id="9f2ff-203">`Boolean` `true` ve `false`</span><span class="sxs-lookup"><span data-stu-id="9f2ff-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="9f2ff-204">`long` veya `double` sayılar</span><span class="sxs-lookup"><span data-stu-id="9f2ff-204">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="9f2ff-205">`DateTime` tarihler</span><span class="sxs-lookup"><span data-stu-id="9f2ff-205">Dates to `DateTime`</span></span>
* <span data-ttu-id="9f2ff-206">`string` dizeler</span><span class="sxs-lookup"><span data-stu-id="9f2ff-206">Strings to `string`</span></span>
* <span data-ttu-id="9f2ff-207">`JsonElement` diğer her şey</span><span class="sxs-lookup"><span data-stu-id="9f2ff-207">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="9f2ff-208">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-208">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="9f2ff-209">Aşağıda `Object` özelliklere sahip örnek bir tür verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-209">Here's an example type with `Object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="9f2ff-210">Seri durumdan çıkarılacak aşağıdaki JSON örneği, `DateTime`, `long`ve `string`olarak seri durumdan çıkarılacak değerler içerir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-210">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="9f2ff-211">Özel dönüştürücü olmadan, seri durumdan çıkarma her özelliğe bir `JsonElement` koyar.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-211">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="9f2ff-212">`System.Text.Json.Serialization` ad alanındaki [birim testleri klasörü](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) , nesne özelliklerine seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-212">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="9f2ff-213">Dize olmayan anahtarla destek sözlüğü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-213">Support Dictionary with non-string key</span></span>

<span data-ttu-id="9f2ff-214">Sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>`içindir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-214">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="9f2ff-215">Diğer bir deyişle, anahtar bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-215">That is, the key must be a string.</span></span> <span data-ttu-id="9f2ff-216">Anahtar olarak bir tamsayı veya başka tür içeren bir sözlüğü desteklemek için özel bir dönüştürücü gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-216">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="9f2ff-217">Aşağıdaki kod, `Dictionary<Enum,TValue>`ile birlikte çalışarak özel bir dönüştürücüyü gösterir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-217">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="9f2ff-218">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-218">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="9f2ff-219">Dönüştürücü aşağıdaki `Enum`kullanan aşağıdaki sınıfın `TemperatureRanges` özelliğini seri hale getirebilirsiniz ve serisini kaldıramıyor:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-219">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="9f2ff-220">Seri hale getirme işleminden alınan JSON çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-220">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="9f2ff-221">`System.Text.Json.Serialization` ad alanındaki [birim testleri klasörü](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) , dize dışı anahtar sözlüklerini işleyen özel dönüştürücülere daha fazla örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-221">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="9f2ff-222">Polimorfik serisini destekler</span><span class="sxs-lookup"><span data-stu-id="9f2ff-222">Support polymorphic deserialization</span></span>

<span data-ttu-id="9f2ff-223">[Polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) özel bir dönüştürücü gerektirmez, ancak seri durumundan çıkarma özel bir dönüştürücü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-223">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="9f2ff-224">Örneğin, `Employee` ve `Customer` türetilmiş sınıflarla `Person` soyut bir temel sınıfınız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-224">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="9f2ff-225">Polimorfik seri kaldırma, tasarım zamanında `Person` serisini kaldırma hedefi olarak belirtebileceğiniz ve `Customer` ve JSON 'daki `Employee` nesnelerinin çalışma zamanında doğru şekilde seri durumdan çıkarılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-225">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="9f2ff-226">Seri durumdan çıkarma sırasında, JSON 'da gerekli türü tanımlayan ipuçları bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-226">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="9f2ff-227">Kullanılabilir ipuçları türleri her senaryoya göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-227">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="9f2ff-228">Örneğin, bir Ayrıştırıcı özelliği kullanılabilir olabilir veya belirli bir özelliğin varlığına veya yokluğuna güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-228">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="9f2ff-229">`System.Text.Json` geçerli sürümü, çok biçimli seri kaldırma senaryolarının nasıl işleneceğini belirtmek için öznitelikler sağlamaz, bu nedenle özel dönüştürücüler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-229">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="9f2ff-230">Aşağıdaki kod, temel sınıfı, iki türetilmiş sınıfı ve bunlar için özel bir dönüştürücüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-230">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="9f2ff-231">Dönüştürücü, çok biçimli seri kaldırma işlemi yapmak için bir Ayrıştırıcı özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-231">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="9f2ff-232">Tür ayrıştırıcısı sınıf tanımlarında değildir, ancak serileştirme sırasında oluşturulur ve seri durumundan çıkarma sırasında okunabilir.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-232">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="9f2ff-233">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-233">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="9f2ff-234">Dönüştürücü, serileştirme için aynı dönüştürücü kullanılarak oluşturulan JSON serisini kaldıramıyor, örneğin:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-234">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

## <a name="other-custom-converter-samples"></a><span data-ttu-id="9f2ff-235">Diğer özel dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="9f2ff-235">Other custom converter samples</span></span>

<span data-ttu-id="9f2ff-236">`System.Text.Json.Serialization` kaynak kodundaki [birim testleri klasörü](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) , aşağıdakiler gibi diğer özel dönüştürücü örneklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-236">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="9f2ff-237">seri durumdan çıkarma sırasında null değeri 0 olarak dönüştüren `Int32` Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-237">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="9f2ff-238">seri durumdan çıkarma sırasında hem dize hem de sayı değerlerine izin veren `Int32` Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-238">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="9f2ff-239">`Enum` Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-239">`Enum` converter</span></span>
* <span data-ttu-id="9f2ff-240">dış veri kabul eden `List<T>` Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-240">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="9f2ff-241">virgülle ayrılmış bir sayı listesi ile birlikte kullanılan `Long[]` Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="9f2ff-241">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="9f2ff-242">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9f2ff-242">Additional resources</span></span>

* [<span data-ttu-id="9f2ff-243">System. Text. JSON genel bakış</span><span class="sxs-lookup"><span data-stu-id="9f2ff-243">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="9f2ff-244">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="9f2ff-244">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="9f2ff-245">System. Text. JSON kullanma</span><span class="sxs-lookup"><span data-stu-id="9f2ff-245">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="9f2ff-246">Yerleşik dönüştürücüler için kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="9f2ff-246">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="9f2ff-247">`System.Text.Json` yönelik özel dönüştürücüler ile ilgili GitHub sorunları</span><span class="sxs-lookup"><span data-stu-id="9f2ff-247">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="9f2ff-248">36639 özel dönüştürücüler tanıtımı</span><span class="sxs-lookup"><span data-stu-id="9f2ff-248">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="9f2ff-249">Nesne serisini kaldırma hakkında 38713</span><span class="sxs-lookup"><span data-stu-id="9f2ff-249">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="9f2ff-250">dize olmayan anahtar sözlükleri hakkında 40120</span><span class="sxs-lookup"><span data-stu-id="9f2ff-250">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="9f2ff-251">çok biçimli seri kaldırma hakkında 37787</span><span class="sxs-lookup"><span data-stu-id="9f2ff-251">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
