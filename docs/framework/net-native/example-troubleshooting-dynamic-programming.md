---
title: 'Örnek: Dinamik Programlama Sorunlarını Giderme'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: ff179854066d024a89cb5a84a19d0b9bb054d6e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128448"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Örnek: Dinamik Programlama Sorunlarını Giderme
> [!NOTE]
> Bu konu, yayın öncesi yazılım olan .NET Native geliştirici önizlemesine başvurur. Önizlemeyi [Microsoft Connect Web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerekir).  
  
 .NET Native araç zinciri kullanılarak geliştirilen uygulamalardaki tüm meta veri arama hatalarının bir özel durum sonucu yoktur.  Bazıları, bir uygulamada öngörülemeyen yollarla bildirimde bulunabilir.  Aşağıdaki örnek, null bir nesneye başvuruda bulunarak oluşan bir erişim ihlali gösterir:  
  
```output
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
  
 [Kullanmaya](getting-started-with-net-native.md)başlama konusunun "eksik meta verileri el ile çözümleme" bölümünde özetlenen üç adımlı yaklaşımı kullanarak bu özel durumu gidermeye deneyelim.  
  
## <a name="what-was-the-app-doing"></a>Uygulama ne yapıyordu?  
 İlk nottaki şey, `async` yığının tabanında anahtar sözcük makinelerdir.  Bir yöntemde uygulamanın gerçekten ne yaptığını belirlemek soruna neden olabilir `async` . yığın, kaynak çağrının bağlamını kaybettiğinden ve `async` kodu farklı bir iş parçacığında çalıştırmıştır. Bununla birlikte, uygulamanın ilk sayfasını yüklemeye çalıştığı anlaşıyoruz.  Uygulamasında `NavigationArgs.Setup` , aşağıdaki kod erişim ihlaline neden oldu:  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 Bu örnekte, `LayoutVM` özelliği `AppViewModel.Current` **null**idi.  Bazı meta veri yokluğu, hafif davranış farkına neden oldu ve uygulamanın beklendiği gibi küme yerine başlatılmamış bir özellik ile sonuçlandı.  Kodda başlatılmış olması gereken bir kesme noktası ayarlamak `LayoutVM` durumunda ışık oluşturabilir.  Ancak, `LayoutVM` türünün olduğunu unutmayın `App.Core.ViewModels.Layout.LayoutApplicationVM` .  Şu ana kadar Rd. xml dosyasında olan tek metaveri yönergesi şu şekilde bulunur:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Hata için olası bir aday, `App.Core.ViewModels.Layout.LayoutApplicationVM` farklı bir ad alanında olduğu için meta veriler eksik.  
  
 Bu durumda, sorunu çözen bir çalışma zamanı yönergesi ekleme `App.Core.ViewModels` . Kök neden, null döndüren yöntemine yönelik bir API çağrısıdır <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> ve **null**uygulama kilitlenme gerçekleşene kadar sorunu sessizce yok sayılır.  
  
 Dinamik programlamada, .NET Native altında yansıma API 'Leri kullanırken iyi bir uygulama <xref:System.Type.GetType%2A?displayProperty=nameWithType> hata durumunda özel durum oluşturan aşırı yüklemeleri kullanmaktır.  
  
## <a name="is-this-an-isolated-case"></a>Bu yalıtılmış bir durumdur mi?  
 Kullanırken diğer sorunlar da oluşabilir `App.Core.ViewModels` .  Eksik bir meta veri özel durumunun belirlenmesi ve düzeltilmesi ya da zaman tasarrufu ve daha büyük bir tür sınıfı için yönergeler eklenmesi gerektiğine karar vermelisiniz.  Burada, `dynamic` `App.Core.ViewModels` Çıkış ikilisinin elde edilen boyut artışı bir sorun değilse, için meta verileri eklemek en iyi yaklaşım olabilir.  
  
## <a name="could-the-code-be-rewritten"></a>Kod yeniden yazılabilir mi?  
 Uygulamanın `typeof(LayoutApplicationVM)` yerine kullanıldıysa `Type.GetType("LayoutApplicationVM")` , araç zinciri korunan `browse` meta verileri olabilir.  Ancak, `invoke` tür örneği oluşturulurken [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumuna yol gösteren meta verileri hala oluşturmazdı. Özel durumu engellemek için, ad alanı veya ilkeyi belirten tür için bir çalışma zamanı yönergesi eklemeniz gerekir `dynamic` . Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Örnek: Veri Bağlama Sırasında Özel Durum İşleme](example-handling-exceptions-when-binding-data.md)
