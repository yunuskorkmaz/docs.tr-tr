---
title: İle türetilmiş sınıfların özelliklerini serileştirme System.Text.Json
description: .NET 'teki JSON 'a serileştirirken ve seri durumdan çıkarılırken çok biçimli nesneleri serileştirme hakkında bilgi edinin.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: b5053ae6be725e82f4389eb1793fc3b5a1028d34
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478855"
---
# <a name="how-to-serialize-properties-of-derived-classes-with-systemtextjson"></a><span data-ttu-id="d2705-103">İle türetilmiş sınıfların özelliklerini serileştirme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d2705-103">How to serialize properties of derived classes with System.Text.Json</span></span>

<span data-ttu-id="d2705-104">Bu makalede, türetilmiş sınıfların özelliklerini ad alanıyla serileştirerek öğrenirsiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="d2705-104">In this article, you will learn how to serialize properties of derived classes with the `System.Text.Json` namespace.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="d2705-105">Türetilmiş sınıfların serileştirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2705-105">Serialize properties of derived classes</span></span>

<span data-ttu-id="d2705-106">Çok biçimli bir tür hiyerarşisinin serileştirilmesi _desteklenmiyor._</span><span class="sxs-lookup"><span data-stu-id="d2705-106">Serialization of a polymorphic type hierarchy is _not_ supported.</span></span> <span data-ttu-id="d2705-107">Örneğin, bir özellik bir arabirim ya da soyut sınıf olarak tanımlanmışsa, çalışma zamanı türü ek özelliklere sahip olsa bile yalnızca arabirim veya soyut sınıf üzerinde tanımlanan özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="d2705-107">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="d2705-108">Bu davranışın istisnaları, bu bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2705-108">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="d2705-109">Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız olduğunu varsayalım `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="d2705-109">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFDerived":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFDerived":::

<span data-ttu-id="d2705-110">Ve derleme zamanında yöntemin tür bağımsız değişkeninin `Serialize` Şu olduğunu varsayalım `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="d2705-110">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeDefault":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeDefault":::

<span data-ttu-id="d2705-111">Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir nesne olsa bile Özellik serileştirilmez `WeatherForecastDerived` .</span><span class="sxs-lookup"><span data-stu-id="d2705-111">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="d2705-112">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="d2705-112">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="d2705-113">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d2705-113">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="d2705-114">Yukarıdaki örnekteki türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="d2705-114">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="d2705-115"><xref:System.Text.Json.JsonSerializer.Serialize%2A>Çalışma zamanında türü belirtmenize olanak sağlayan aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="d2705-115">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeGetType":::
  :::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeGetType":::

* <span data-ttu-id="d2705-116">Seri hale getirilecek nesneyi bildirin `object` .</span><span class="sxs-lookup"><span data-stu-id="d2705-116">Declare the object to be serialized as `object`.</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeObject":::
  :::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeObject":::

<span data-ttu-id="d2705-117">Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` ÖZELLIĞIN JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="d2705-117">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="d2705-118">Bu yaklaşımlar yalnızca kök nesnenin seri hale getirilmesi için, bu kök nesnenin özellikleri için değil, polimorfik serileştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2705-118">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="d2705-119">Bunları tür olarak tanımlarsanız alt düzey nesneler için polimorfik serileştirme alabilirsiniz `object` .</span><span class="sxs-lookup"><span data-stu-id="d2705-119">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="d2705-120">Örneğin, `WeatherForecast` sınıfınızın, tür olarak tanımlanabilen adında bir özelliği olduğunu varsayalım `PreviousForecast` `WeatherForecast` `object` :</span><span class="sxs-lookup"><span data-stu-id="d2705-120">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPrevious":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithPrevious":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPreviousAsObject":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithPreviousAsObject":::

<span data-ttu-id="d2705-121">`PreviousForecast`Özelliği bir örneği içeriyorsa `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="d2705-121">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="d2705-122">Serileştirmede JSON çıktısı `WeatherForecastWithPrevious` **içermez** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="d2705-122">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="d2705-123">Serileştirmede JSON çıktısı `WeatherForecastWithPreviousAsObject` **dahildir** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="d2705-123">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="d2705-124">Seri hale getirmek için `WeatherForecastWithPreviousAsObject` , `Serialize<object>` ya da `GetType` kök nesnesi türetilmiş bir tür olabilecek bir nesne olmadığından çağırmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d2705-124">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="d2705-125">Aşağıdaki kod örneği, `Serialize<object>` veya çağırmaz `GetType` :</span><span class="sxs-lookup"><span data-stu-id="d2705-125">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeSecondLevel":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeSecondLevel":::

<span data-ttu-id="d2705-126">Yukarıdaki kod doğru şekilde serileştirir `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="d2705-126">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="d2705-127">Özellikleri, arabirimler ile birlikte tanımlamaya yönelik aynı yaklaşım `object` .</span><span class="sxs-lookup"><span data-stu-id="d2705-127">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="d2705-128">Aşağıdaki arabirime ve uygulamaya sahip olduğunuzu ve uygulama örnekleri içeren özelliklerle bir sınıfı seri hale getirmek istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="d2705-128">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/IForecast.cs":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/IForecast.vb":::

<span data-ttu-id="d2705-129">Bir örneğini serileştirçalıştığınızda `Forecasts` , yalnızca `Tuesday` `WindSpeed` özelliğini gösterir, çünkü `Tuesday` Şu şekilde tanımlanır `object` :</span><span class="sxs-lookup"><span data-stu-id="d2705-129">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeInterface":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeInterface":::

<span data-ttu-id="d2705-130">Aşağıdaki örnek, önceki koddan elde edilen JSON 'u göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="d2705-130">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

> [!NOTE]
> <span data-ttu-id="d2705-131">Bu makale serileştirilmesi için serileştirme, seri durumdan çıkarma ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="d2705-131">This article is about serialization, not deserialization.</span></span> <span data-ttu-id="d2705-132">Polimorfik seri kaldırma desteklenmez, ancak geçici bir çözüm olarak, örneğin, çok [biçimli seri kaldırma desteği](system-text-json-converters-how-to.md#support-polymorphic-deserialization)gibi özel bir dönüştürücü yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2705-132">Polymorphic deserialization is not supported, but as a workaround you can write a custom converter, such as the example in [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2705-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2705-133">See also</span></span>

* [<span data-ttu-id="d2705-134">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="d2705-134">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="d2705-135">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="d2705-135">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="d2705-136">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2705-136">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="d2705-137">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d2705-137">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="d2705-138">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2705-138">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="d2705-139">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="d2705-139">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="d2705-140">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="d2705-140">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="d2705-141">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="d2705-141">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="d2705-142">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="d2705-142">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="d2705-143">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="d2705-143">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="d2705-144">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d2705-144">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="d2705-145">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2705-145">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="d2705-146">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="d2705-146">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="d2705-147">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="d2705-147">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="d2705-148">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="d2705-148">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="d2705-149">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d2705-149">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="d2705-150">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="d2705-150">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
