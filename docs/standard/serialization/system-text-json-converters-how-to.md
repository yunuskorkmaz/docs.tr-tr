---
title: JSON serileştirme-.NET için özel dönüştürücüler yazma
description: 'Ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturmayı öğrenin :::no-loc(System.Text.Json)::: .'
ms.date: 01/10/2020
no-loc:
- ':::no-loc(System.Text.Json):::'
- ':::no-loc(Newtonsoft.Json):::'
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: ba6b61232ccf7ed493fe5809e5c0b8ba21091d3d
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329813"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="1ff71-103">.NET 'teki JSON serileştirme (sıralama) için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="1ff71-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="1ff71-104">Bu makalede, ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturma işlemi gösterilmektedir <xref::::no-loc(System.Text.Json):::> .</span><span class="sxs-lookup"><span data-stu-id="1ff71-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref::::no-loc(System.Text.Json):::> namespace.</span></span> <span data-ttu-id="1ff71-105">Uygulamasına giriş için `:::no-loc(System.Text.Json):::` bkz. [.net 'te JSON serileştirme ve seri durumdan çıkarma](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="1ff71-105">For an introduction to `:::no-loc(System.Text.Json):::`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="1ff71-106">*Dönüştürücü* bir nesneyi veya BIR değeri JSON öğesine veya bir değere dönüştüren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="1ff71-107">`:::no-loc(System.Text.Json):::`Ad alanı, JavaScript temel elemanlarına eşleyen en basit türlerin yerleşik Dönüştürücülerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-107">The `:::no-loc(System.Text.Json):::` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="1ff71-108">Özel dönüştürücüler yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1ff71-108">You can write custom converters:</span></span>

* <span data-ttu-id="1ff71-109">Yerleşik dönüştürücünün varsayılan davranışını geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="1ff71-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="1ff71-110">Örneğin, `DateTime` varsayılan ıso 8601-1:2019 biçimi yerine, değerlerin aa/gg/yyyy biçiminde temsil olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ff71-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="1ff71-111">Özel bir değer türünü desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="1ff71-111">To support a custom value type.</span></span> <span data-ttu-id="1ff71-112">Örneğin, bir `PhoneNumber` struct.</span><span class="sxs-lookup"><span data-stu-id="1ff71-112">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="1ff71-113">Ayrıca, `:::no-loc(System.Text.Json):::` geçerli sürüme dahil olmayan işlevlerle özelleştirmek veya genişletmek için özel dönüştürücüler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ff71-113">You can also write custom converters to customize or extend `:::no-loc(System.Text.Json):::` with functionality not included in the current release.</span></span> <span data-ttu-id="1ff71-114">Bu makalenin ilerleyen bölümlerinde aşağıdaki senaryolar ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="1ff71-114">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="1ff71-115">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="1ff71-115">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="1ff71-116">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="1ff71-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="1ff71-117">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="1ff71-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="1ff71-118">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="1ff71-118">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="1ff71-119">[Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="1ff71-119">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="1ff71-120">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="1ff71-120">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="1ff71-121">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="1ff71-121">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

## <a name="custom-converter-patterns"></a><span data-ttu-id="1ff71-122">Özel dönüştürücü desenleri</span><span class="sxs-lookup"><span data-stu-id="1ff71-122">Custom converter patterns</span></span>

<span data-ttu-id="1ff71-123">Özel dönüştürücü oluşturmak için iki desen vardır: temel desen ve fabrika düzeni.</span><span class="sxs-lookup"><span data-stu-id="1ff71-123">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="1ff71-124">Fabrika deseninin türü `Enum` veya açık genel türleri işleyen dönüştürücüler içindir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-124">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="1ff71-125">Temel model, genel olmayan ve kapalı genel türler içindir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-125">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="1ff71-126">Örneğin, aşağıdaki türler için dönüştürücüler fabrika deseninin olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1ff71-126">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="1ff71-127">Temel model tarafından işlenebilen türlerin bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1ff71-127">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="1ff71-128">Temel model, bir türü işleyebileceğini bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ff71-128">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="1ff71-129">Fabrika stili, çalışma zamanında, belirli bir türün gerekli olduğunu ve uygun dönüştürücüyü dinamik olarak oluşturduğunu belirleyen bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ff71-129">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="1ff71-130">Örnek temel dönüştürücü</span><span class="sxs-lookup"><span data-stu-id="1ff71-130">Sample basic converter</span></span>

<span data-ttu-id="1ff71-131">Aşağıdaki örnek, varolan bir veri türü için varsayılan Serileştirmeyi geçersiz kılan bir dönüştürücütür.</span><span class="sxs-lookup"><span data-stu-id="1ff71-131">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="1ff71-132">Dönüştürücü özellikler için aa/gg/yyyy biçimini kullanır `DateTimeOffset` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-132">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="1ff71-133">Örnek fabrika deseninin Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="1ff71-133">Sample factory pattern converter</span></span>

<span data-ttu-id="1ff71-134">Aşağıdaki kod ile birlikte çalışarak özel bir dönüştürücüyü gösterir `Dictionary<Enum,TValue>` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-134">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="1ff71-135">İlk genel tür parametresi olduğundan ve ikincisi açık olduğundan, kod fabrika düzeniyle uyar `Enum` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-135">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="1ff71-136">`CanConvert`Yöntemi `true` yalnızca, bir türü olan, yalnızca `Dictionary` iki genel parametre içeren için döndürür `Enum` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-136">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="1ff71-137">İç dönüştürücü, için çalışma zamanında hangi türün sağlandığını işlemek üzere mevcut bir dönüştürücüyü alır `TValue` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-137">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="1ff71-138">Yukarıdaki kod, bu makalede daha sonra [dize olmayan anahtarla destek sözlüğünde](#support-dictionary-with-non-string-key) gösterilenle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-138">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="1ff71-139">Temel kalıbı izlemeye yönelik adımlar</span><span class="sxs-lookup"><span data-stu-id="1ff71-139">Steps to follow the basic pattern</span></span>

<span data-ttu-id="1ff71-140">Aşağıdaki adımlarda, temel kalıbı izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1ff71-140">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="1ff71-141">Öğesinden türetilen, <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601> `T` seri hale getirilecek ve seri durumdan çıkarılacak bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ff71-141">Create a class that derives from <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="1ff71-142">`Read`Gelen JSON serisini kaldırmak ve türe dönüştürmek için yöntemini geçersiz kılın `T` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-142">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="1ff71-143"><xref::::no-loc(System.Text.Json):::.Utf8JsonReader>JSON 'ı okumak için yöntemine geçirilen öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-143">Use the <xref::::no-loc(System.Text.Json):::.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="1ff71-144">`Write`Türündeki gelen nesneyi seri hale getirmek için yöntemini geçersiz kılın `T` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-144">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="1ff71-145"><xref::::no-loc(System.Text.Json):::.Utf8JsonWriter>JSON yazmak için yöntemine geçirilen öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-145">Use the <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="1ff71-146">`CanConvert`Yöntemi yalnızca gerektiğinde geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-146">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="1ff71-147">Varsayılan uygulama, `true` dönüştürülecek tür tür olduğunda döndürür `T` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-147">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="1ff71-148">Bu nedenle, yalnızca türü destekleyen dönüştürücüler `T` Bu yöntemi geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-148">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="1ff71-149">Bu yöntemi geçersiz kılmanın gerekli olduğu dönüştürücünün bir örneği için, bu makalenin ilerleyen kısımlarında yer alan [polimorfik serisini kaldırma](#support-polymorphic-deserialization) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-149">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="1ff71-150">[Yerleşik dönüştürücüler kaynak koduna](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters/) , özel dönüştürücüler yazmak için başvuru uygulamaları olarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ff71-150">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="1ff71-151">Fabrika deseninin izlenmesi için adımlar</span><span class="sxs-lookup"><span data-stu-id="1ff71-151">Steps to follow the factory pattern</span></span>

<span data-ttu-id="1ff71-152">Aşağıdaki adımlarda, fabrika modelini izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1ff71-152">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="1ff71-153">Öğesinden türetilen bir sınıf oluşturun <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterFactory> .</span><span class="sxs-lookup"><span data-stu-id="1ff71-153">Create a class that derives from <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="1ff71-154">`CanConvert`Dönüştürülecek tür dönüştürücünün işleyebileceği bir ise true döndürecek şekilde yöntemi geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-154">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="1ff71-155">Örneğin, dönüştürücü için ise `List<T>` yalnızca `List<int>` , `List<string>` ve işleyebilir `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-155">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="1ff71-156">`CreateConverter`Çalışma zamanında belirtilen tür dönüşümü işleyecek bir dönüştürücü sınıfının örneğini döndürmek için yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-156">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="1ff71-157">Yöntemin örnekleyen Converter sınıfını oluşturun `CreateConverter` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-157">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="1ff71-158">Açık genel türler için fabrika deseninin olması gerekir çünkü bir nesneyi bir dizeye ve bu dizeden dönüştürecek kod tüm türler için aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-158">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="1ff71-159">Açık genel tür için bir dönüştürücü ( `List<T>` Örneğin,), arka plandaki bir kapalı genel tür (örneğin) için bir dönüştürücü oluşturmaktır `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-159">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="1ff71-160">Dönüştürücünün işleyebileceği her bir kapalı genel türü işlemek için kodun yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-160">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="1ff71-161">`Enum`Tür, açık bir genel türe benzer: bir dönüştürücünün, `Enum` `Enum` arka planda belirli bir (örneğin,) bir dönüştürücü oluşturması gerekir `WeekdaysEnum` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-161">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="1ff71-162">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="1ff71-162">Error handling</span></span>

<span data-ttu-id="1ff71-163">Hata işleme kodunda bir özel durum oluşturmanız gerekiyorsa, <xref::::no-loc(System.Text.Json):::.JsonException> ileti olmadan bir ileti yerleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="1ff71-163">If you need to throw an exception in error-handling code, consider throwing a <xref::::no-loc(System.Text.Json):::.JsonException> without a message.</span></span> <span data-ttu-id="1ff71-164">Bu özel durum türü otomatik olarak, hataya neden olan JSON bölümünün yolunu içeren bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ff71-164">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="1ff71-165">Örneğin, ifade `throw new JsonException();` Aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:</span><span class="sxs-lookup"><span data-stu-id="1ff71-165">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```output
Unhandled exception. :::no-loc(System.Text.Json):::.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="1ff71-166">Bir ileti sağlarsanız (örneğin, `throw new JsonException("Error occurred")` özel durum hala özelliğindeki yolu sağlar <xref::::no-loc(System.Text.Json):::.JsonException.Path> .</span><span class="sxs-lookup"><span data-stu-id="1ff71-166">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref::::no-loc(System.Text.Json):::.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="1ff71-167">Özel dönüştürücüyü kaydetme</span><span class="sxs-lookup"><span data-stu-id="1ff71-167">Register a custom converter</span></span>

<span data-ttu-id="1ff71-168">*Register* `Serialize` Ve yöntemlerinin onu kullanmasını sağlamak için özel bir dönüştürücü kaydedin `Deserialize` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-168">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="1ff71-169">Aşağıdaki yaklaşımlardan birini seçin:</span><span class="sxs-lookup"><span data-stu-id="1ff71-169">Choose one of the following approaches:</span></span>

* <span data-ttu-id="1ff71-170">Koleksiyona Converter sınıfının bir örneğini ekleyin <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.Converters?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1ff71-170">Add an instance of the converter class to the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="1ff71-171">Özel dönüştürücü gerektiren özelliklere [[Jsonconverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-171">Apply the [[JsonConverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="1ff71-172">[[Jsonconverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) özniteliğini bir sınıfa veya özel bir değer türünü temsil eden bir yapıya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-172">Apply the [[JsonConverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="1ff71-173">Kayıt örneği-dönüştürücüler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="1ff71-173">Registration sample - Converters collection</span></span>

<span data-ttu-id="1ff71-174">Aşağıda <xref:System.ComponentModel.DateTimeOffsetConverter> , türü özellikler için varsayılan değer sağlayan bir örnek verilmiştir <xref:System.DateTimeOffset> :</span><span class="sxs-lookup"><span data-stu-id="1ff71-174">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="1ff71-175">Aşağıdaki türde bir örneği serileştirdiğinizi varsayın:</span><span class="sxs-lookup"><span data-stu-id="1ff71-175">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="1ff71-176">Özel dönüştürücünün kullanıldığını gösteren bir JSON çıkışı örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1ff71-176">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="1ff71-177">Aşağıdaki kod özel dönüştürücüyü kullanarak seri durumdan çıkarmak için aynı yaklaşımı kullanır `DateTimeOffset` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-177">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="1ff71-178">Kayıt örneği-[JsonConverter] bir özellikte</span><span class="sxs-lookup"><span data-stu-id="1ff71-178">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="1ff71-179">Aşağıdaki kod, özelliği için özel bir dönüştürücü seçer `Date` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-179">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="1ff71-180">Seri hale getirilecek kod şunu kullanılmasını `WeatherForecastWithConverterAttribute` gerektirmez `JsonSerializeOptions.Converters` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-180">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="1ff71-181">Seri durumdan çıkarılacak kod ayrıca kullanımını gerektirmez `Converters` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-181">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="1ff71-182">Kayıt örneği-[JsonConverter] bir tür üzerinde</span><span class="sxs-lookup"><span data-stu-id="1ff71-182">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="1ff71-183">Bir struct oluşturan ve özniteliği uygulayan kod aşağıda verilmiştir `[JsonConverter]` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-183">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="1ff71-184">Önceki yapı için özel dönüştürücü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1ff71-184">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="1ff71-185">`[JsonConvert]`Yapı üzerindeki özniteliği özel dönüştürücüyü türü özellikler için varsayılan olarak kaydeder `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-185">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="1ff71-186">Dönüştürücü, `TemperatureCelsius` seri hale getirmek veya serisini kaldırmak için aşağıdaki türün özelliğinde otomatik olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="1ff71-186">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="1ff71-187">Dönüştürücü kayıt önceliği</span><span class="sxs-lookup"><span data-stu-id="1ff71-187">Converter registration precedence</span></span>

<span data-ttu-id="1ff71-188">Serileştirme veya seri durumundan çıkarma sırasında, en yüksek öncelikten en düşüğe doğru listelenen her bir JSON öğesi için bir dönüştürücü seçilir:</span><span class="sxs-lookup"><span data-stu-id="1ff71-188">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="1ff71-189">`[JsonConverter]` bir özelliğe uygulandı.</span><span class="sxs-lookup"><span data-stu-id="1ff71-189">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="1ff71-190">Koleksiyona eklenen bir dönüştürücü `Converters` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-190">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="1ff71-191">`[JsonConverter]` özel bir değer türüne veya POCO 'a uygulandı.</span><span class="sxs-lookup"><span data-stu-id="1ff71-191">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="1ff71-192">Bir tür için birden çok özel dönüştürücü `Converters` koleksiyonda kayıtlıysa, için true döndüren ilk dönüştürücü `CanConvert` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-192">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="1ff71-193">Yalnızca uygulanabilir özel dönüştürücü kayıtlı değilse, yerleşik bir dönüştürücü seçilir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-193">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="1ff71-194">Yaygın senaryolar için dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="1ff71-194">Converter samples for common scenarios</span></span>

<span data-ttu-id="1ff71-195">Aşağıdaki bölümlerde, yerleşik işlevlerin sağlamadığı bazı yaygın senaryolar ele alan dönüştürücü örnekleri sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-195">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="1ff71-196">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="1ff71-196">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="1ff71-197">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="1ff71-197">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="1ff71-198">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="1ff71-198">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="1ff71-199">[Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="1ff71-199">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="1ff71-200">[Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="1ff71-200">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="1ff71-201">[Polimorfik serisini destekler](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="1ff71-201">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="1ff71-202">[Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="1ff71-202">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="1ff71-203">Çıkartılan türlerin nesne özelliklerine serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="1ff71-203">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="1ff71-204">Türünde bir özelliğe seri durumdan çıkarılırken `object` bir `JsonElement` nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ff71-204">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="1ff71-205">Bunun nedeni, seri hale getiricinin oluşturulacak CLR türünü bilmeyeceği ve tahmin etmeye çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="1ff71-205">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="1ff71-206">Örneğin, bir JSON özelliğinde "true" varsa, seri hale getirici değerin bir olduğunu `Boolean` ve bir öğede "01/01/2019" varsa, seri hale getiricinin bir olduğunu çıkarmaz `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-206">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="1ff71-207">Tür çıkarımı yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-207">Type inference can be inaccurate.</span></span> <span data-ttu-id="1ff71-208">Seri hale getirici, ondalık noktası olmayan bir JSON numarasını ayrıştırır `long` . Bu, değerin başlangıçta veya olarak seri hale getirilmediği durumlarda Aralık dışı sorunlara yol açabilir `ulong` `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-208">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="1ff71-209">`double`Sayı ilk olarak bir olarak seri hale getirilemediği takdirde, ondalık noktası olan bir sayının ayrıştırmasında duyarlık kaybolabilir `decimal` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-209">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="1ff71-210">Tür çıkarımı gerektiren senaryolar için aşağıdaki kod, özellikler için özel bir dönüştürücü gösterir `object` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-210">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="1ff71-211">Kod dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="1ff71-211">The code converts:</span></span>

* <span data-ttu-id="1ff71-212">`true` ve `false` için `Boolean`</span><span class="sxs-lookup"><span data-stu-id="1ff71-212">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="1ff71-213">Ondalık olmayan sayılar `long`</span><span class="sxs-lookup"><span data-stu-id="1ff71-213">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="1ff71-214">Ondalık sayı olan sayılar `double`</span><span class="sxs-lookup"><span data-stu-id="1ff71-214">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="1ff71-215">Tarihler `DateTime`</span><span class="sxs-lookup"><span data-stu-id="1ff71-215">Dates to `DateTime`</span></span>
* <span data-ttu-id="1ff71-216">Dizeler `string`</span><span class="sxs-lookup"><span data-stu-id="1ff71-216">Strings to `string`</span></span>
* <span data-ttu-id="1ff71-217">Diğer her şey `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="1ff71-217">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="1ff71-218">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="1ff71-218">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="1ff71-219">Özelliklere sahip örnek bir tür aşağıda verilmiştir `object` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-219">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="1ff71-220">Seri durumdan çıkarılacak aşağıdaki JSON örneği,, ve olarak seri durumdan çıkarılacak değerler `DateTime` içerir `long` `string` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-220">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="1ff71-221">Özel dönüştürücü olmadan, seri durumdan çıkarma `JsonElement` her özelliğe bir koyar.</span><span class="sxs-lookup"><span data-stu-id="1ff71-221">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="1ff71-222">Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) , `:::no-loc(System.Text.Json):::.Serialization` özellikleri seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir `object` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) in the `:::no-loc(System.Text.Json):::.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="1ff71-223">Dize olmayan anahtarla destek sözlüğü</span><span class="sxs-lookup"><span data-stu-id="1ff71-223">Support Dictionary with non-string key</span></span>

<span data-ttu-id="1ff71-224">Sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-224">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="1ff71-225">Diğer bir deyişle, anahtar bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-225">That is, the key must be a string.</span></span> <span data-ttu-id="1ff71-226">Anahtar olarak bir tamsayı veya başka tür içeren bir sözlüğü desteklemek için özel bir dönüştürücü gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-226">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="1ff71-227">Aşağıdaki kod ile birlikte çalışarak özel bir dönüştürücüyü göstermektedir `Dictionary<Enum,TValue>` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-227">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="1ff71-228">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="1ff71-228">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="1ff71-229">Dönüştürücü, aşağıdakileri `TemperatureRanges` kullanan aşağıdaki sınıfın özelliğini seri hale getirebilirsiniz ve serisini kaldıramıyor `Enum` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-229">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="1ff71-230">Seri hale getirme işleminden alınan JSON çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="1ff71-230">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="1ff71-231">Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) , `:::no-loc(System.Text.Json):::.Serialization` dize dışı anahtar sözlüklerini işleyen özel dönüştürücülere daha fazla örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-231">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) in the `:::no-loc(System.Text.Json):::.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="1ff71-232">Polimorfik serisini destekler</span><span class="sxs-lookup"><span data-stu-id="1ff71-232">Support polymorphic deserialization</span></span>

<span data-ttu-id="1ff71-233">Yerleşik özellikler sınırlı sayıda [polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) sağlar, ancak hiçbir zaman serisini kaldırma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="1ff71-233">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="1ff71-234">Seri durumdan çıkarma özel bir dönüştürücü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-234">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="1ff71-235">Örneğin, `Person` `Employee` ve türetilmiş sınıflar içeren bir soyut taban sınıfınız olduğunu varsayalım `Customer` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-235">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="1ff71-236">Polimorfik seri kaldırma, tasarım zamanında `Person` , seri durumdan çıkarma hedefi olarak belirtebileceğiniz ve `Customer` `Employee` JSON 'daki nesnelerin çalışma zamanında doğru bir şekilde seri durumdan çıkarılması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-236">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="1ff71-237">Seri durumdan çıkarma sırasında, JSON 'da gerekli türü tanımlayan ipuçları bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-237">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="1ff71-238">Kullanılabilir ipuçları türleri her senaryoya göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-238">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="1ff71-239">Örneğin, bir Ayrıştırıcı özelliği kullanılabilir olabilir veya belirli bir özelliğin varlığına veya yokluğuna güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ff71-239">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="1ff71-240">Geçerli sürümü, çok `:::no-loc(System.Text.Json):::` biçimli seri kaldırma senaryolarını nasıl işleyeceğinizi belirtmek için öznitelikler sağlamaz, bu nedenle özel dönüştürücüler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-240">The current release of `:::no-loc(System.Text.Json):::` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="1ff71-241">Aşağıdaki kod, temel sınıfı, iki türetilmiş sınıfı ve bunlar için özel bir dönüştürücüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-241">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="1ff71-242">Dönüştürücü, çok biçimli seri kaldırma işlemi yapmak için bir Ayrıştırıcı özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-242">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="1ff71-243">Tür ayrıştırıcısı sınıf tanımlarında değildir, ancak serileştirme sırasında oluşturulur ve seri durumundan çıkarma sırasında okunabilir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-243">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="1ff71-244">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="1ff71-244">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="1ff71-245">Dönüştürücü, serileştirme için aynı dönüştürücü kullanılarak oluşturulan JSON serisini kaldıramıyor, örneğin:</span><span class="sxs-lookup"><span data-stu-id="1ff71-245">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="1ff71-246">Yukarıdaki örnekteki dönüştürücü kodu, her bir özelliği el ile okur ve yazar.</span><span class="sxs-lookup"><span data-stu-id="1ff71-246">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="1ff71-247">Bir alternatif, çalışmanın bir `Deserialize` kısmını çağırmak veya yapmak için kullanılır `Serialize` .</span><span class="sxs-lookup"><span data-stu-id="1ff71-247">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="1ff71-248">Bir örnek için, [Bu StackOverflow gönderisini](https://stackoverflow.com/a/59744873/12509023)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="1ff71-248">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="1ff71-249">Yığın için gidiş dönüş desteği\<T></span><span class="sxs-lookup"><span data-stu-id="1ff71-249">Support round trip for Stack\<T></span></span>

<span data-ttu-id="1ff71-250">Bir JSON dizesini bir nesneye serisini çıkardıysanız <xref:System.Collections.Generic.Stack%601> ve sonra bu nesneyi serileştirmek istiyorsanız, yığının içeriği ters sıralardır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-250">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="1ff71-251">Bu davranış, aşağıdaki türler ve arabirim için ve bunlardan türetilmiş Kullanıcı tanımlı türler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="1ff71-251">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="1ff71-252">Yığın içinde orijinal sırayı koruyan serileştirme ve serisini desteklemek için özel bir dönüştürücü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-252">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="1ff71-253">Aşağıdaki kod, nesnelerinden ve nesnelerden gidiş dönüşü sağlayan özel bir dönüştürücüyü gösterir `Stack<T>` :</span><span class="sxs-lookup"><span data-stu-id="1ff71-253">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="1ff71-254">Aşağıdaki kod dönüştürücüyü kaydeder:</span><span class="sxs-lookup"><span data-stu-id="1ff71-254">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="handle-null-values"></a><span data-ttu-id="1ff71-255">Null değerleri işleme</span><span class="sxs-lookup"><span data-stu-id="1ff71-255">Handle null values</span></span>

<span data-ttu-id="1ff71-256">Varsayılan olarak, seri hale getirici null değerlerini aşağıdaki şekilde işler:</span><span class="sxs-lookup"><span data-stu-id="1ff71-256">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="1ff71-257">Başvuru türleri ve `Nullable<T>` türleri için:</span><span class="sxs-lookup"><span data-stu-id="1ff71-257">For reference types and `Nullable<T>` types:</span></span>

  * <span data-ttu-id="1ff71-258">`null`Serileştirme sırasında özel Dönüştürücülerine geçmez.</span><span class="sxs-lookup"><span data-stu-id="1ff71-258">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="1ff71-259">`JsonTokenType.Null`Seri durumdan çıkarma sırasında özel Dönüştürücülerine geçmez.</span><span class="sxs-lookup"><span data-stu-id="1ff71-259">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="1ff71-260">`null`Seri durumdan çıkarma üzerine bir örnek döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ff71-260">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="1ff71-261">`null`Serileştirme üzerinde doğrudan yazıcıya yazar.</span><span class="sxs-lookup"><span data-stu-id="1ff71-261">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="1ff71-262">Null yapılamayan değer türleri için:</span><span class="sxs-lookup"><span data-stu-id="1ff71-262">For non-nullable value types:</span></span>

  * <span data-ttu-id="1ff71-263">`JsonTokenType.Null`Seri durumdan çıkarma sırasında özel Dönüştürücülerine geçer.</span><span class="sxs-lookup"><span data-stu-id="1ff71-263">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="1ff71-264">(Özel dönüştürücü yoksa, `JsonException` tür için iç dönüştürücü tarafından bir özel durum oluşturulur.)</span><span class="sxs-lookup"><span data-stu-id="1ff71-264">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="1ff71-265">Bu null işleme davranışı öncelikle, dönüştürücünün ek bir çağrısını atlayarak performansı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-265">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="1ff71-266">Ayrıca, `null` her `Read` ve `Write` yöntemi geçersiz kılmanın başlangıcında olup olmadığını kontrol etmek için null yapılabilir türler için dönüştürücüler zorlamaktan kaçınır.</span><span class="sxs-lookup"><span data-stu-id="1ff71-266">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="1ff71-267">Bir özel dönüştürücünün `null` bir başvuru veya değer türü için işlemesini sağlamak için, <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi, döndürecek şekilde geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="1ff71-267">To enable a custom converter to handle `null` for a reference or value type, override <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="1ff71-268">Diğer özel dönüştürücü örnekleri</span><span class="sxs-lookup"><span data-stu-id="1ff71-268">Other custom converter samples</span></span>

<span data-ttu-id="1ff71-269">' [Den :::no-loc(Newtonsoft.Json)::: :::no-loc(System.Text.Json)::: geçiş](system-text-json-migrate-from-newtonsoft-how-to.md) , özel dönüştürücülerin ek örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1ff71-269">The [Migrate from :::no-loc(Newtonsoft.Json)::: to :::no-loc(System.Text.Json):::](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="1ff71-270">Kaynak kodundaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) `:::no-loc(System.Text.Json):::.Serialization` , gibi diğer özel dönüştürücü örneklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="1ff71-270">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) in the `:::no-loc(System.Text.Json):::.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="1ff71-271">[Seri durumdan çıkarma sırasında null değeri 0 olarak dönüştüren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="1ff71-271">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="1ff71-272">[Seri durumdan çıkarma sırasında hem dize hem de sayı değerlerine izin veren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="1ff71-272">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="1ff71-273">[Sabit Listesi Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="1ff71-273">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="1ff71-274">[\<T>Dış verileri kabul eden liste Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="1ff71-274">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="1ff71-275">[Long [] bir sayı listesi ile birlikte çalışma](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="1ff71-275">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="1ff71-276">Varolan bir yerleşik dönüştürücünün davranışını değiştiren bir dönüştürücü yapmanız gerekiyorsa, varolan dönüştürücünün özelleştirme için bir başlangıç noktası olarak sunmak üzere [kaynak kodunu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters) alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ff71-276">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1ff71-277">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1ff71-277">Additional resources</span></span>

* <span data-ttu-id="1ff71-278">[Yerleşik dönüştürücüler için kaynak kodu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="1ff71-278">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="1ff71-279">İçinde DateTime ve DateTimeOffset desteği :::no-loc(System.Text.Json):::</span><span class="sxs-lookup"><span data-stu-id="1ff71-279">DateTime and DateTimeOffset support in :::no-loc(System.Text.Json):::</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="1ff71-280">:::no-loc(System.Text.Json)::: bakýþ</span><span class="sxs-lookup"><span data-stu-id="1ff71-280">:::no-loc(System.Text.Json)::: overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="1ff71-281">Nasıl kullanılır :::no-loc(System.Text.Json):::</span><span class="sxs-lookup"><span data-stu-id="1ff71-281">How to use :::no-loc(System.Text.Json):::</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="1ff71-282">Öğesinden geçiş :::no-loc(Newtonsoft.Json):::</span><span class="sxs-lookup"><span data-stu-id="1ff71-282">How to migrate from :::no-loc(Newtonsoft.Json):::</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* <span data-ttu-id="1ff71-283">[:::no-loc(System.Text.Json)::: API başvurusu](xref::::no-loc(System.Text.Json):::)</span><span class="sxs-lookup"><span data-stu-id="1ff71-283">[:::no-loc(System.Text.Json)::: API reference](xref::::no-loc(System.Text.Json):::)</span></span>
* <span data-ttu-id="1ff71-284">[:::no-loc(System.Text.Json):::. Serileştirme API başvurusu](xref::::no-loc(System.Text.Json):::.Serialization)</span><span class="sxs-lookup"><span data-stu-id="1ff71-284">[:::no-loc(System.Text.Json):::.Serialization API reference](xref::::no-loc(System.Text.Json):::.Serialization)</span></span>
<!-- * [:::no-loc(System.Text.Json)::: roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/roadmap/README.md)-->
