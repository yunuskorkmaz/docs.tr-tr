---
title: 'Örnek: Veri Bağlama Sırasında Özel Durum İşleme'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e7a0929bd5f07c5a1986d885984332d692d3a9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415885"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="fc2ac-102">Örnek: Veri Bağlama Sırasında Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="fc2ac-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
>  <span data-ttu-id="fc2ac-103">Bu konuda, .NET Native Geliştirici yayın öncesi bir yazılım olan Önizleme, ifade eder.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="fc2ac-104">Önizlemesi'nden indirebileceğiniz [Microsoft Connect Web sitesi](https://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerekir).</span><span class="sxs-lookup"><span data-stu-id="fc2ac-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="fc2ac-105">Aşağıdaki örnek nasıl giderileceğini gösterir bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) uygulama ile derlendiğinde oluşturulan özel durum [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zincirinizi veri bağlama dener.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-105">The following example shows how to resolve a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain tries to bind data.</span></span> <span data-ttu-id="fc2ac-106">Özel durum bilgilerini şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fc2ac-106">Here’s the exception information:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="fc2ac-107">İlişkili çağrı yığını şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fc2ac-107">Here's the associated call stack:</span></span>  
  
```  
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
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="fc2ac-108">Uygulama neler oldu?</span><span class="sxs-lookup"><span data-stu-id="fc2ac-108">What was the app doing?</span></span>  
 <span data-ttu-id="fc2ac-109">Gelen temel yığın çerçevelerini [Windows.UI.Xaml](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) ad alanı belirtmek XAML işleme altyapısı çalışıyordu.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-109">At the base of the stack, frames from the [Windows.UI.Xaml](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="fc2ac-110">Kullanımını <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> olan meta veriler temizlendi türünde bir özelliğin değerinin yansıma tabanlı bir arama yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="fc2ac-111">Meta veri yönergesi sağlayan ilk adımı eklemek için olacaktır `serialize` türü için meta veri özelliklerini tüm erişilebilir olacak şekilde:</span><span class="sxs-lookup"><span data-stu-id="fc2ac-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="fc2ac-112">Bu, yalıtılmış bir durum mu?</span><span class="sxs-lookup"><span data-stu-id="fc2ac-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="fc2ac-113">Bu senaryoda, veri bağlama tamamlanmamış meta verileri için bir tane varsa `ViewModel`, diğerleri için bir çok olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="fc2ac-114">Kod, uygulamanın görünüm modelleri tek bir şekilde yapılandırılırsa `App.ViewModels` ad alanı, daha genel bir çalışma zamanı yönerge kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fc2ac-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="fc2ac-115">Kod, yansıma kullanmayı yazılması?</span><span class="sxs-lookup"><span data-stu-id="fc2ac-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="fc2ac-116">Veri bağlama yansıma yoğun olduğundan, yansıma önlemek için kodu değiştirme uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="fc2ac-117">Ancak, yolu belirtmek için vardır `ViewModel` XAML sayfası araç zincirinizi ilişkilendirebilirsiniz böylece doğru türde özellik bağlamalarla derleme zamanı ve çalışma zamanı yönerge kullanmadan meta verileri tut.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="fc2ac-118">Örneğin, uygulayabilirsiniz [Windows.UI.Xaml.Data.BindableAttribute](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) öznitelik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-118">For example, you could apply the [Windows.UI.Xaml.Data.BindableAttribute](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) attribute on properties.</span></span> <span data-ttu-id="fc2ac-119">Bu, XAML derleyicinin arama gerekli bilgileri oluşturmak ve Default.rd.xml dosyasındaki bir çalışma zamanı yönerge gerektiren önler.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2ac-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2ac-120">See Also</span></span>  
 [<span data-ttu-id="fc2ac-121">Başlarken</span><span class="sxs-lookup"><span data-stu-id="fc2ac-121">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="fc2ac-122">Örnek: Dinamik Programlama Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="fc2ac-122">Example: Troubleshooting Dynamic Programming</span></span>](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
