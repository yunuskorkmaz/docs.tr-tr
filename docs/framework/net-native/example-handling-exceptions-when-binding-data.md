---
title: 'Örnek: Veri Bağlama Sırasında Özel Durum İşleme'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: b774d1bce4f4d1c03258ed44b27d3871e7c5275f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181028"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="fd909-102">Örnek: Veri Bağlama Sırasında Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="fd909-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
> <span data-ttu-id="fd909-103">Bu konu, yayın öncesi yazılım olan .NET Yerel Geliştirici Önizlemesi'ni ifade eder.</span><span class="sxs-lookup"><span data-stu-id="fd909-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="fd909-104">Önizlemeyi Microsoft Connect [web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerektirir).</span><span class="sxs-lookup"><span data-stu-id="fd909-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="fd909-105">Aşağıdaki örnek, .NET Yerel araç zinciriyle derlenen bir uygulama verileri bağlamaya çalıştığında atılan [Bir Eksik MetadataException](missingmetadataexception-class-net-native.md) özel durum nasıl çözüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd909-105">The following example shows how to resolve a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the .NET Native tool chain tries to bind data.</span></span> <span data-ttu-id="fd909-106">İstisna bilgileri aşağıda veda eder:</span><span class="sxs-lookup"><span data-stu-id="fd909-106">Here’s the exception information:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="fd909-107">İlişkili çağrı yığını aşağıda veda edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fd909-107">Here's the associated call stack:</span></span>  
  
```output
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="fd909-108">Uygulama ne yapıyordu?</span><span class="sxs-lookup"><span data-stu-id="fd909-108">What was the app doing?</span></span>  
 <span data-ttu-id="fd909-109">Yığının tabanında, ad alanından <xref:Windows.UI.Xaml?displayProperty=nameWithType> kareler XAML işleme altyapısının çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd909-109">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="fd909-110"><xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> Yöntemin kullanımı, meta verileri kaldırılan türde bir özelliğin değerinin yansıma tabanlı bir görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd909-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="fd909-111">Meta veri yönergesi sağlamanın ilk `serialize` adımı, özelliklerinin tümüne erişilebilmek için tür için meta veri eklemek olacaktır:</span><span class="sxs-lookup"><span data-stu-id="fd909-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="fd909-112">Bu münferit bir dava mı?</span><span class="sxs-lookup"><span data-stu-id="fd909-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="fd909-113">Bu senaryoda, veri bağlama biri `ViewModel`için eksik meta veri varsa, diğerleri için de olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd909-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="fd909-114">Kod, uygulamanın görünüm modellerinin tümü `App.ViewModels` ad alanında olacak şekilde yapılandırılmışsa, daha genel bir çalışma zamanı yönergesi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fd909-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="fd909-115">Kod yansımayı kullanmamak için yeniden yazılabilir mi?</span><span class="sxs-lookup"><span data-stu-id="fd909-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="fd909-116">Veri bağlama yansıma yoğun olduğundan, yansımayı önlemek için kodu değiştirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="fd909-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="fd909-117">Ancak, araç zincirinin `ViewModel` özellik bağlamalarını derleme zamanında doğru türle ilişkilendirebilmeleri ve çalışma zamanı yönergesi kullanmadan meta verileri tutabilmesi için XAML sayfasına belirtmenin yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="fd909-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="fd909-118">Örneğin, özellikler üzerinde <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd909-118">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="fd909-119">Bu, XAML derleyicisinin gerekli arama bilgilerini oluşturmasına neden olur ve Varsayılan.rd.xml dosyasında çalışma zamanı yönergesi gerektirmesini önler.</span><span class="sxs-lookup"><span data-stu-id="fd909-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd909-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd909-120">See also</span></span>

- [<span data-ttu-id="fd909-121">Başlarken</span><span class="sxs-lookup"><span data-stu-id="fd909-121">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="fd909-122">Örnek: Dinamik Programlama Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="fd909-122">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)
