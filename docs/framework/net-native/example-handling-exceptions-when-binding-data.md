---
title: "Örnek: Veri Bağlama Sırasında Özel Durum İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2714d53426bfee22b3d83d76b766816d9bc9d60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="3e54e-102">Örnek: Veri Bağlama Sırasında Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="3e54e-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
>  <span data-ttu-id="3e54e-103">Bu konu, .NET yerel geliştirici yayın öncesi yazılımı olan Önizleme, ifade eder.</span><span class="sxs-lookup"><span data-stu-id="3e54e-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="3e54e-104">Önizlemesi'nden indirebilirsiniz [Microsoft Connect Web](http://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerektirir).</span><span class="sxs-lookup"><span data-stu-id="3e54e-104">You can download the preview from the [Microsoft Connect website](http://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="3e54e-105">Aşağıdaki örnekte nasıl çözümleneceğini gösterir bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ile bir uygulama derlenmiş olmadığında oluşan özel durum [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri veri bağlama dener.</span><span class="sxs-lookup"><span data-stu-id="3e54e-105">The following example shows how to resolve a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain tries to bind data.</span></span> <span data-ttu-id="3e54e-106">Özel durum bilgilerini şöyledir:</span><span class="sxs-lookup"><span data-stu-id="3e54e-106">Here’s the exception information:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="3e54e-107">İlişkili çağrı yığını şöyledir:</span><span class="sxs-lookup"><span data-stu-id="3e54e-107">Here's the associated call stack:</span></span>  
  
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
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="3e54e-108">Uygulama yaptıklarını edildi?</span><span class="sxs-lookup"><span data-stu-id="3e54e-108">What was the app doing?</span></span>  
 <span data-ttu-id="3e54e-109">Gelen yığın tabanına çerçeve [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) ad alanı belirtmek XAML işleme altyapısı çalışıyordu.</span><span class="sxs-lookup"><span data-stu-id="3e54e-109">At the base of the stack, frames from the [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="3e54e-110">Kullanımını <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> bir özelliğin değeri, meta veriler temizlendi türündeki yansıma tabanlı bir arama yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e54e-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="3e54e-111">Meta veri yönergesi sağlayan ilk adımı eklemek için olacaktır `serialize` türü için meta veri özelliklerini tüm erişilebilir; böylece:</span><span class="sxs-lookup"><span data-stu-id="3e54e-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="3e54e-112">Bu yalıtılmış bir durumdur?</span><span class="sxs-lookup"><span data-stu-id="3e54e-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="3e54e-113">Veri bağlama tamamlanmamış meta verileri için bir tane varsa, bu senaryoda, `ViewModel`, diğerleri için bir çok olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e54e-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="3e54e-114">Kod, uygulamanın görünümü modelleri tüm bulunan şekilde yapılandırılırsa `App.ViewModels` ad alanı, daha genel bir çalışma zamanı yönerge kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e54e-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="3e54e-115">Kod yansıma kullanmayacak şekilde yeniden yazılmıştır?</span><span class="sxs-lookup"><span data-stu-id="3e54e-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="3e54e-116">Veri bağlama yansıma yoğunluklu olduğundan, yansıma önlemek için kodu değiştirme uygun değil.</span><span class="sxs-lookup"><span data-stu-id="3e54e-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="3e54e-117">Ancak, belirtmek için yol vardır `ViewModel` için XAML sayfası araç zinciri ilişkilendirebilirsiniz böylece doğru türde özelliği bağlamalarla derleme zamanı ve çalışma zamanı yönerge kullanmadan meta verileri tut.</span><span class="sxs-lookup"><span data-stu-id="3e54e-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="3e54e-118">Örneğin, uygulayabilir [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) özellikleri özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3e54e-118">For example, you could apply the [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) attribute on properties.</span></span> <span data-ttu-id="3e54e-119">Bu gerekli arama bilgileri oluşturmak XAML derleyici neden olur ve Default.rd.xml dosyasındaki bir çalışma zamanı yönerge gerektiren önler.</span><span class="sxs-lookup"><span data-stu-id="3e54e-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e54e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e54e-120">See Also</span></span>  
 [<span data-ttu-id="3e54e-121">Başlarken</span><span class="sxs-lookup"><span data-stu-id="3e54e-121">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="3e54e-122">Örnek: Dinamik Programlama Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="3e54e-122">Example: Troubleshooting Dynamic Programming</span></span>](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
