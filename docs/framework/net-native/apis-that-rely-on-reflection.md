---
title: Yansıma kullanan API'ler
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 1d8daceb6b744b984f86b011ad7952d0da583a79
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181087"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="c0bec-102">Yansıma kullanan API'ler</span><span class="sxs-lookup"><span data-stu-id="c0bec-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="c0bec-103">Bazı durumlarda, kodda yansıma kullanımı belirgin değildir ve bu nedenle .NET Native araç zinciri çalışma zamanında gereken meta verileri korumaz.</span><span class="sxs-lookup"><span data-stu-id="c0bec-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="c0bec-104">Bu konu, yansıma API 'sinin bir parçası olarak kabul edilmeyen ancak yansıma dosyasını başarıyla yürütmek için kullanan bazı ortak API 'Leri veya ortak programlama düzenlerini ele almaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0bec-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="c0bec-105">Bunları kaynak kodunuzda kullanıyorsanız, bu API 'lere yapılan çağrıların bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu veya çalışma zamanında başka bir özel durum oluşturmaması için çalışma zamanı yönergeleri (. RD. xml) dosyasına bunlarla ilgili bilgi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0bec-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="c0bec-106">Type. MakeGenericType yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0bec-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="c0bec-107">`AppClass<T>` <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> Aşağıdaki gibi bir kod kullanarak yöntemini çağırarak bir genel türü dinamik olarak oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c0bec-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="c0bec-108">Bu kodun çalışma zamanında başarılı olması için birkaç meta veri öğesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c0bec-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="c0bec-109">İlki, `Browse` örneklenmemiş genel türün meta verilerdir `AppClass<T>` :</span><span class="sxs-lookup"><span data-stu-id="c0bec-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="c0bec-110">Bu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntem çağrısının başarılı olmasını ve geçerli bir nesne döndürmesini sağlar <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="c0bec-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="c0bec-111">Ancak, örneklenmemiş genel tür için meta veriler eklediğinizde bile <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemi çağırmak bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c0bec-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="c0bec-112">Bu işlem, performans nedenleriyle aşağıdaki tür için meta veriler kaldırıldığından yürütülemiyor:</span><span class="sxs-lookup"><span data-stu-id="c0bec-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="c0bec-113">`App1.AppClass`1<System. Int32>'.</span><span class="sxs-lookup"><span data-stu-id="c0bec-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="c0bec-114">`Activate`Belirli bir örnek oluşturma için meta verileri eklemek üzere çalışma zamanı yönergeleri dosyasına aşağıdaki çalışma zamanı yönergesini ekleyebilirsiniz `AppClass<T>` <xref:System.Int32?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="c0bec-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="c0bec-115">Her farklı örnekleme `AppClass<T>` , yöntemiyle oluşturulduysa ve statik olarak kullanılmazsa ayrı bir yönerge gerektirir <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c0bec-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="c0bec-116">MethodInfo. MakeGenericMethod yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0bec-116">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="c0bec-117">`Class1`Genel bir yöntemi olan bir sınıf verildiğinde `GetMethod<T>(T t)` , aşağıdaki gibi bir `GetMethod` kod kullanılarak yansıma aracılığıyla çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="c0bec-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="c0bec-118">Başarılı bir şekilde çalıştırmak için, bu kod birçok meta veri öğesi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c0bec-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="c0bec-119">`Browse`yöntemi çağırmak istediğiniz türün meta verileri.</span><span class="sxs-lookup"><span data-stu-id="c0bec-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="c0bec-120">`Browse`çağırmak istediğiniz metodun meta verileri.</span><span class="sxs-lookup"><span data-stu-id="c0bec-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="c0bec-121">Ortak bir yöntem ise, `Browse` kapsayan tür için ortak meta verileri eklemek de yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="c0bec-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="c0bec-122">Çağırmak istediğiniz metodun dinamik meta verileri, böylece yansıma çağırma temsilcisi .NET Native araç zinciri tarafından kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="c0bec-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="c0bec-123">Yöntemi için dinamik meta veriler eksikse, yöntemi çağrıldığında aşağıdaki özel durum oluşur <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="c0bec-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="c0bec-124">Aşağıdaki çalışma zamanı yönergeleri tüm gerekli meta verilerin kullanılabilir olduğundan emin olur:</span><span class="sxs-lookup"><span data-stu-id="c0bec-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="c0bec-125">`MethodInstantiation`Dinamik olarak çağrılan metodun her farklı örneklemesi için bir yönerge gereklidir ve `Arguments` öğe, her farklı örnekleme bağımsız değişkenini yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c0bec-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="c0bec-126">Array. CreateInstance ve Type. MakeTypeArray yöntemleri</span><span class="sxs-lookup"><span data-stu-id="c0bec-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="c0bec-127">Aşağıdaki örnek, <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> yöntemlerini bir tür üzerinde çağırır `Class1` .</span><span class="sxs-lookup"><span data-stu-id="c0bec-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="c0bec-128">Hiçbir dizi meta verisi yoksa, aşağıdaki hata oluşur:</span><span class="sxs-lookup"><span data-stu-id="c0bec-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="c0bec-129">`Browse`dizi türü için meta veriler dinamik olarak örneğini oluşturmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c0bec-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="c0bec-130">Aşağıdaki çalışma zamanı yönergesi dinamik örneklemeyi sağlar `Class1[]` .</span><span class="sxs-lookup"><span data-stu-id="c0bec-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0bec-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0bec-131">See also</span></span>

- [<span data-ttu-id="c0bec-132">Başlarken</span><span class="sxs-lookup"><span data-stu-id="c0bec-132">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="c0bec-133">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c0bec-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
