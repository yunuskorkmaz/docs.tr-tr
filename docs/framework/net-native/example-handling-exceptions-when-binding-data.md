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
ms.openlocfilehash: 18f2d06d3a6974b913af663a38a6155b38422232
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="example-handling-exceptions-when-binding-data"></a>Örnek: Veri Bağlama Sırasında Özel Durum İşleme
> [!NOTE]
>  Bu konu, .NET yerel geliştirici yayın öncesi yazılımı olan Önizleme, ifade eder. Önizlemesi'nden indirebilirsiniz [Microsoft Connect Web](http://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerektirir).  
  
 Aşağıdaki örnekte nasıl çözümleneceğini gösterir bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ile bir uygulama derlenmiş olmadığında oluşan özel durum [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri veri bağlama dener. Özel durum bilgilerini şöyledir:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 İlişkili çağrı yığını şöyledir:  
  
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
  
## <a name="what-was-the-app-doing"></a>Uygulama yaptıklarını edildi?  
 Gelen yığın tabanına çerçeve [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) ad alanı belirtmek XAML işleme altyapısı çalışıyordu.   Kullanımını <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> bir özelliğin değeri, meta veriler temizlendi türündeki yansıma tabanlı bir arama yöntemi gösterir.  
  
 Meta veri yönergesi sağlayan ilk adımı eklemek için olacaktır `serialize` türü için meta veri özelliklerini tüm erişilebilir; böylece:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Bu yalıtılmış bir durumdur?  
 Veri bağlama tamamlanmamış meta verileri için bir tane varsa, bu senaryoda, `ViewModel`, diğerleri için bir çok olabilir.  Kod, uygulamanın görünümü modelleri tüm bulunan şekilde yapılandırılırsa `App.ViewModels` ad alanı, daha genel bir çalışma zamanı yönerge kullanabilirsiniz:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Kod yansıma kullanmayacak şekilde yeniden yazılmıştır?  
 Veri bağlama yansıma yoğunluklu olduğundan, yansıma önlemek için kodu değiştirme uygun değil.  
  
 Ancak, belirtmek için yol vardır `ViewModel` için XAML sayfası araç zinciri ilişkilendirebilirsiniz böylece doğru türde özelliği bağlamalarla derleme zamanı ve çalışma zamanı yönerge kullanmadan meta verileri tut.  Örneğin, uygulayabilir [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) özellikleri özniteliği. Bu gerekli arama bilgileri oluşturmak XAML derleyici neden olur ve Default.rd.xml dosyasındaki bir çalışma zamanı yönerge gerektiren önler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Örnek: Dinamik programlama sorunlarını giderme](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
