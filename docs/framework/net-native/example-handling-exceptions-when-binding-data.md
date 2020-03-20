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
# <a name="example-handling-exceptions-when-binding-data"></a>Örnek: Veri Bağlama Sırasında Özel Durum İşleme
> [!NOTE]
> Bu konu, yayın öncesi yazılım olan .NET Yerel Geliştirici Önizlemesi'ni ifade eder. Önizlemeyi Microsoft Connect [web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerektirir).  
  
 Aşağıdaki örnek, .NET Yerel araç zinciriyle derlenen bir uygulama verileri bağlamaya çalıştığında atılan [Bir Eksik MetadataException](missingmetadataexception-class-net-native.md) özel durum nasıl çözüleceğini gösterir. İstisna bilgileri aşağıda veda eder:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 İlişkili çağrı yığını aşağıda veda edebilirsiniz:  
  
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
  
## <a name="what-was-the-app-doing"></a>Uygulama ne yapıyordu?  
 Yığının tabanında, ad alanından <xref:Windows.UI.Xaml?displayProperty=nameWithType> kareler XAML işleme altyapısının çalıştığını gösterir.   <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> Yöntemin kullanımı, meta verileri kaldırılan türde bir özelliğin değerinin yansıma tabanlı bir görünümünü gösterir.  
  
 Meta veri yönergesi sağlamanın ilk `serialize` adımı, özelliklerinin tümüne erişilebilmek için tür için meta veri eklemek olacaktır:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Bu münferit bir dava mı?  
 Bu senaryoda, veri bağlama biri `ViewModel`için eksik meta veri varsa, diğerleri için de olabilir.  Kod, uygulamanın görünüm modellerinin tümü `App.ViewModels` ad alanında olacak şekilde yapılandırılmışsa, daha genel bir çalışma zamanı yönergesi kullanabilirsiniz:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Kod yansımayı kullanmamak için yeniden yazılabilir mi?  
 Veri bağlama yansıma yoğun olduğundan, yansımayı önlemek için kodu değiştirmek mümkün değildir.  
  
 Ancak, araç zincirinin `ViewModel` özellik bağlamalarını derleme zamanında doğru türle ilişkilendirebilmeleri ve çalışma zamanı yönergesi kullanmadan meta verileri tutabilmesi için XAML sayfasına belirtmenin yolları vardır.  Örneğin, özellikler üzerinde <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> öznitelik uygulayabilirsiniz. Bu, XAML derleyicisinin gerekli arama bilgilerini oluşturmasına neden olur ve Varsayılan.rd.xml dosyasında çalışma zamanı yönergesi gerektirmesini önler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Örnek: Dinamik Programlama Sorunlarını Giderme](example-troubleshooting-dynamic-programming.md)
