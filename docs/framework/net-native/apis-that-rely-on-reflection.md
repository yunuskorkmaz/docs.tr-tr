---
title: Yansıma kullanan API'ler
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ec1280f3b7ba25367fac21d5160046915636a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076867"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="96213-102">Yansıma kullanan API'ler</span><span class="sxs-lookup"><span data-stu-id="96213-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="96213-103">Bazı durumlarda, kodda yansıma kullanımına açıktır, değildir ve bu nedenle [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri, çalışma zamanında gereken meta verileri korumak değil.</span><span class="sxs-lookup"><span data-stu-id="96213-103">In some cases, the use of reflection in code isn't obvious, and so the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="96213-104">Bu konu, bazı ortak API'ler veya, yansıma API'si bir parçası olarak kabul değildir ancak, başarılı bir şekilde yürütmek için yansıma kullanan ortak programlama modellerini kapsar.</span><span class="sxs-lookup"><span data-stu-id="96213-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="96213-105">Kaynak kodunuzu kullanmak, bunlar hakkında bilgi için çalışma zamanı yönergeleri ekleyebilirsiniz (. rd.xml) bu API'lere giden çağrıların değil throw dosyasını bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durum ya da diğer bazı özel çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="96213-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="96213-106">Type.MakeGenericType yöntemi</span><span class="sxs-lookup"><span data-stu-id="96213-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="96213-107">Dinamik olarak bir genel tür örneği oluşturabilir `AppClass<T>` çağırarak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> aşağıdakine benzer bir kod kullanarak yöntemi:</span><span class="sxs-lookup"><span data-stu-id="96213-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="96213-108">Çeşitli meta veri öğelerinin çalışma zamanında başarılı olması bu kod için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="96213-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="96213-109">İlk `Browse` örneklenmemiş genel türü için meta verileri `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="96213-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="96213-110">Böylece <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> metot çağrısı başarılı olması ve geçerli bir döndürmek için <xref:System.Type> nesne.</span><span class="sxs-lookup"><span data-stu-id="96213-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="96213-111">Ancak bile örneklenmemiş genel türü için meta verileri eklediğinizde, çağırma <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntem bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durum:</span><span class="sxs-lookup"><span data-stu-id="96213-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 <span data-ttu-id="96213-112">Çalışma zamanı yönergeleri dosyasına eklemek için aşağıdaki çalışma zamanı yönerge ekleyebilirsiniz `Activate` belirli örneklemesi için meta verileri `AppClass<T>` , <xref:System.Int32?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="96213-112">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="96213-113">Üzerinden farklı her örneklemesi `AppClass<T>` ayrı yönergesi ile oluşturuluyorsa gerektirir <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemi ve statik olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="96213-113">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="96213-114">MethodInfo.MakeGenericMethod yöntemi</span><span class="sxs-lookup"><span data-stu-id="96213-114">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="96213-115">Bir sınıf verilen `Class1` ile genel yöntem `GetMethod<T>(T t)`, `GetMethod` yansıma yoluyla bu kodu kullanarak çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="96213-115">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="96213-116">Başarılı bir şekilde çalıştırmak için bu kodu çeşitli meta veri öğeleri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="96213-116">To run successfully, this code requires several items of metadata:</span></span>  
  
-   <span data-ttu-id="96213-117">`Browse` yöntem çağırmak istediğinizde türü için meta veriler.</span><span class="sxs-lookup"><span data-stu-id="96213-117">`Browse` metadata for the type whose method you want to call.</span></span>  
  
-   <span data-ttu-id="96213-118">`Browse` aramak istediğiniz yöntem için meta veriler.</span><span class="sxs-lookup"><span data-stu-id="96213-118">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="96213-119">Genel bir yöntem ise, genel ekleme `Browse` kapsayan türü için meta verileri yöntemi çok içerir.</span><span class="sxs-lookup"><span data-stu-id="96213-119">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
-   <span data-ttu-id="96213-120">Dinamik meta veriler, istediğiniz çağırmak için böylece yansıma çağırma temsilcisi tarafından kaldırılmaz yöntemi [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="96213-120">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="96213-121">Dinamik meta veriler için yöntem eksikse, şu özel durum oluşan <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> yöntemi çağrılır:</span><span class="sxs-lookup"><span data-stu-id="96213-121">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="96213-122">Aşağıdaki çalışma zamanı yönergeleri gerekli tüm meta veriler kullanılabilir olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="96213-122">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="96213-123">A `MethodInstantiation` yönergesi her farklı örneğinin dinamik olarak çağrılan yöntem için gereklidir ve `Arguments` öğesi her farklı örneklemesine değişken yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="96213-123">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="96213-124">Array.CreateInstance ve Type.MakeTypeArray yöntemleri</span><span class="sxs-lookup"><span data-stu-id="96213-124">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="96213-125">Aşağıdaki örnek çağrıları <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> bir türündeki yöntemlere `Class1`.</span><span class="sxs-lookup"><span data-stu-id="96213-125">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="96213-126">Dizi meta veri işlemi varsa, aşağıdaki hata oluşur:</span><span class="sxs-lookup"><span data-stu-id="96213-126">If no array metadata is present, the following error results:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="96213-127">`Browse` dizi türü için meta verilerini dinamik olarak oluşturmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="96213-127">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="96213-128">Dinamik örneklemesi aşağıdaki çalışma zamanı yönerge sağlar `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="96213-128">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="96213-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96213-129">See also</span></span>

- [<span data-ttu-id="96213-130">Başlarken</span><span class="sxs-lookup"><span data-stu-id="96213-130">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="96213-131">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="96213-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
