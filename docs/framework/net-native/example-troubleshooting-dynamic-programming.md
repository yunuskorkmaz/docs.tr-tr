---
title: 'Örnek: Dinamik Programlama Sorunlarını Giderme'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5de4388f4d3c4117ed71abd9741d2616638038d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="example-troubleshooting-dynamic-programming"></a>Örnek: Dinamik Programlama Sorunlarını Giderme
> [!NOTE]
>  Bu konu, .NET yerel geliştirici yayın öncesi yazılımı olan Önizleme, ifade eder. Önizlemesi'nden indirebilirsiniz [Microsoft Connect Web](http://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerektirir).  
  
 Tüm meta veri arama hataları kullanılarak geliştirilen uygulamalardaki [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı bir özel durum zinciri sonuçlanır.  Bazı uygulama öngörülemeyen şekillerde bildirilebilir.  Aşağıdaki örnek, null bir nesne başvurarak neden bir erişim ihlali gösterir:  
  
```  
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 Bu özel durum "El ile eksik meta veri çözümleme" bölümünde açıklanan üç adımı yaklaşım kullanarak sorun gidermek deneyelim [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Uygulama yaptıklarını edildi?  
 Dikkat edilecek ilk şey `async` yığınının tabanında anahtar sözcüğü makineler.  Hangi uygulamanın gerçekten yapmakta olduğu belirleme bir `async` yöntemi olabilir sorunlu, çünkü yığın kaynak çağrı bağlamında kaybetti ve çalıştırıldı `async` kodu farklı bir iş parçacığı üzerinde. Ancak, biz uygulamayı ilk sayfa yükleme çalışıyor türetme.  Uygulamasında için `NavigationArgs.Setup`, aşağıdaki kodu erişim ihlali neden:  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 Bu örnekte `LayoutVM` özelliği `AppViewModel.Current` olan **null**.  Meta veri bazı yokluğu Zarif davranışı fark neden ve bir özellik kümesi yerine beklenen uygulama olarak başlatılmadı ile sonuçlandı.  Kodda kesme noktası ayarlama nerede `LayoutVM` başlatılmamış ışık durumunuza throw.  Ancak, dikkat edin `LayoutVM`'s türü `App.Core.ViewModels.Layout.LayoutApplicationVM`.  Şu ana kadar rd.xml dosyasında bulunan yalnızca meta veri yönergesi şöyledir:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Hatanın olası bir aday olan `App.Core.ViewModels.Layout.LayoutApplicationVM` farklı bir ad alanında olduğundan meta veriler eksik.  
  
 Bu durumda, bir çalışma zamanı yönerge için ekleme `App.Core.ViewModels` sorunu Çözümlendi. Bir API çağrısı için kök nedeni <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> döndürülen yöntemi **null**, ve bir kilitlenme oluştu dek uygulama sessizce sorun yoksayıldı.  
  
 Dinamik programlama, yansıma API'leri kullanırken iyi bir uygulama içinde altında [!INCLUDE[net_native](../../../includes/net-native-md.md)] kullanmaktır <xref:System.Type.GetType%2A?displayProperty=nameWithType> hatasında bir özel durum aşırı.  
  
## <a name="is-this-an-isolated-case"></a>Bu yalıtılmış bir durumdur?  
 Diğer sorunlar da kullanırken doğabilecek `App.Core.ViewModels`.  Tanımlama ve eksik her meta veri özel durum düzelttikten veya zaman kazandırır ve daha büyük bir sınıf türleri için yönergeleri ekleme değer olup olmadığını karar vermeniz gerekir.  Burada, ekleme `dynamic` meta verilerini `App.Core.ViewModels` elde edilen boyutu artışı çıkış ikili bir sorun yoksa en iyi yaklaşım olabilir.  
  
## <a name="could-the-code-be-rewritten"></a>Kodu yeniden yazılmıştır?  
 Uygulamayı kullandıysa `typeof(LayoutApplicationVM)` yerine `Type.GetType("LayoutApplicationVM")`, araç zinciri muhafaza edilmesini `browse` meta verileri.  Ancak, yine oluşturduktan olmayacaktır `invoke` neden için meta verileri bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) türü örneği oluşturulurken özel durum. Özel durum önlemek için hala bir çalışma zamanı yönerge ad alanı veya belirten türü eklemek olurdu `dynamic` ilkesi. Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Örnek: Veri Bağlama Sırasında Özel Durum İşleme](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
