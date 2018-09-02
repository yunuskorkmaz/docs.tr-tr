---
title: 'Örnek: Dinamik Programlama Sorunlarını Giderme'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a373b946c3ce9f4606e870ae10e23a63398bc9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406375"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Örnek: Dinamik Programlama Sorunlarını Giderme
> [!NOTE]
>  Bu konuda, .NET Native Geliştirici yayın öncesi bir yazılım olan Önizleme, ifade eder. Önizlemesi'nden indirebileceğiniz [Microsoft Connect Web sitesi](https://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerekir).  
  
 Tüm meta veri arama hataları kullanılarak geliştirilen uygulamalarda [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı bir özel durum zinciri sonuçlanır.  Bazı uygulama beklenmedik bir şekilde bildirilebilir.  Aşağıdaki örnek, bir null Nesne başvurarak neden bir erişim ihlali gösterir:  
  
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
  
 Deneyelim "Meta veriler eksik elle Çözümle" bölümünde belirtilen üç adımlı yaklaşım kullanarak bu özel durum sorunlarını giderme [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Uygulama neler oldu?  
 Dikkat edilecek ilk şey `async` temel yığın anahtar sözcüğü makineler.  Hangi uygulamayı gerçekten yapmakta olduğu belirleyen bir `async` yöntemi olabilir sorunlu, çünkü yığın kaynak çağrı bağlamında kesildi ve çalıştırıldı `async` farklı bir iş parçacığında kod. Ancak, uygulama, ilk sayfa çalışıyor çıkarabilir.  İçin uygulamada `NavigationArgs.Setup`, aşağıdaki kod erişim ihlaline neden oldu:  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 Bu örnekte, `LayoutVM` özelliği `AppViewModel.Current` olduğu **null**.  Meta verileri bazı olmaması, hafif bir davranışı fark neden ve yerine küme, beklenen uygulaması olarak başlatılmamış bir özellikte sonuçlandı.  Kodda bir kesme noktası ayarlama burada `LayoutVM` başlatılmamış ışık durumunuza fırlatabilir.  Ancak, unutmayın `LayoutVM`ın türü `App.Core.ViewModels.Layout.LayoutApplicationVM`.  Şu ana kadar rd.xml dosyasında mevcut yalnızca meta veri yönergesi verilmiştir:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Hatanın olası bir aday olan `App.Core.ViewModels.Layout.LayoutApplicationVM` farklı bir ad alanında olduğundan meta veriler eksik.  
  
 Bu durumda, bir çalışma zamanı yönerge için ekleme `App.Core.ViewModels` sorun çözümlenir. Bir API çağrısı için kök nedeni <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> döndürülen yöntemi **null**, ve bir kilitlenme oluştu kadar uygulamayı sessiz bir şekilde sorun yoksayıldı.  
  
 Dinamik programlama, yansıma API'leri kullanırken iyi bir uygulama içinde altında [!INCLUDE[net_native](../../../includes/net-native-md.md)] kullanmaktır <xref:System.Type.GetType%2A?displayProperty=nameWithType> hatasında bir özel durum aşırı yüklemeleri.  
  
## <a name="is-this-an-isolated-case"></a>Bu, yalıtılmış bir durum mu?  
 Diğer sorunları da kullanırken ortaya çıkabilir `App.Core.ViewModels`.  Tanımlama ve eksik her meta veri özel durum düzeltme veya zaman tasarrufu sağlamanıza ve ekleme yönergeleri daha büyük bir sınıf türü için değer olup olmadığını karar vermeniz gerekir.  Burada, ekleme `dynamic` meta verilerini `App.Core.ViewModels` en iyi yaklaşım, sonuçta elde edilen boyutunu artırma çıkış ikili bir sorun yoksa olabilir.  
  
## <a name="could-the-code-be-rewritten"></a>Kod yazılması?  
 Uygulama kullanmışsınız `typeof(LayoutApplicationVM)` yerine `Type.GetType("LayoutApplicationVM")`, araç zincirinizi korunur `browse` meta verileri.  Ancak, yine de oluşturduktan mıydı `invoke` neden için meta verileri bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) türü örneği oluşturulurken özel durum. Özel durum önlemek için yine de ad alanı veya belirten türü için bir çalışma zamanı yönerge eklemeniz gerekir `dynamic` ilkesi. Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Örnek: Veri Bağlama Sırasında Özel Durum İşleme](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
