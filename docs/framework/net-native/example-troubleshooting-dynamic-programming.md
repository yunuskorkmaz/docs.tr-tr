---
title: 'Örnek: Dinamik Programlama Sorunlarını Giderme'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: ff179854066d024a89cb5a84a19d0b9bb054d6e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
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
  
## <a name="what-was-the-app-doing"></a>Uygulama ne yapıyor?  
 İlk şey, yığının tabanında `async` anahtar sözcük makinelerdir.  Bir `async` yöntemde uygulamanın gerçekten ne yaptığını belirlemek soruna neden olabilir, çünkü yığın kaynak çağrının bağlamını kaybetti ve farklı bir iş parçacığında `async` kodunu çalıştırmıştır. Bununla birlikte, uygulamanın ilk sayfasını yüklemeye çalıştığı anlaşıyoruz.  `NavigationArgs.Setup`uygulamada, aşağıdaki kod erişim ihlaline neden oldu:  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 Bu örnekte, `AppViewModel.Current` `LayoutVM` özelliği **null**idi.  Bazı meta veri yokluğu, hafif davranış farkına neden oldu ve uygulamanın beklendiği gibi küme yerine başlatılmamış bir özellik ile sonuçlandı.  `LayoutVM` başlatılmış olması gereken kodda bir kesme noktası ayarlamak durumunda ışık oluşturabilir.  Ancak `LayoutVM`türünün `App.Core.ViewModels.Layout.LayoutApplicationVM`olduğunu unutmayın.  Şu ana kadar Rd. xml dosyasında olan tek metaveri yönergesi şu şekilde bulunur:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Hata için olası bir aday, farklı bir ad alanında olduğundan `App.Core.ViewModels.Layout.LayoutApplicationVM` meta verilerin eksik olmasından kaynaklanır.  
  
 Bu durumda `App.Core.ViewModels` için bir çalışma zamanı yönergesi eklemek sorunu çözdü. Kök neden, **null**döndüren <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metoduna YÖNELIK bir API çağrısıdır ve uygulama kilitlenme gerçekleşene kadar sorunu sessizce yok sayılır.  
  
 Dinamik programlamada, .NET Native altında yansıma API 'Leri kullanırken iyi bir uygulama hata durumunda özel bir durum oluşturan <xref:System.Type.GetType%2A?displayProperty=nameWithType> aşırı yüklemeleri kullanmaktır.  
  
## <a name="is-this-an-isolated-case"></a>Bu yalıtılmış bir durumdur mi?  
 `App.Core.ViewModels`kullanılırken de diğer sorunlar ortaya çıkabilir.  Eksik bir meta veri özel durumunun belirlenmesi ve düzeltilmesi ya da zaman tasarrufu ve daha büyük bir tür sınıfı için yönergeler eklenmesi gerektiğine karar vermelisiniz.  Burada, çıkış ikilisinin elde edilen boyut artışı bir sorun değilse, `App.Core.ViewModels` için `dynamic` meta verileri eklemek en iyi yaklaşım olabilir.  
  
## <a name="could-the-code-be-rewritten"></a>Kod yeniden yazılabilir mi?  
 Uygulama `Type.GetType("LayoutApplicationVM")`yerine `typeof(LayoutApplicationVM)` kullanmıştı, araç zinciri `browse` meta verileri korunabilir.  Ancak, tür örneği oluşturulurken bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu ile birlikte `invoke` meta veri oluşturmuş olmasaydı. Özel durumu engellemek için, ad alanı için bir çalışma zamanı yönergesi veya `dynamic` ilkesini belirten tür için de eklemeniz gerekir. Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Örnek: Veri Bağlama Sırasında Özel Durum İşleme](example-handling-exceptions-when-binding-data.md)
