---
title: 'Örnek: Dinamik Programlama Sorunlarını Giderme'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85d64a5577acdaa15a40ae308eb728d75d6a4c69
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894496"
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
  
 [Kullanmaya](../../../docs/framework/net-native/getting-started-with-net-native.md)başlama konusunun "eksik meta verileri el ile çözümleme" bölümünde özetlenen üç adımlı yaklaşımı kullanarak bu özel durumu gidermeye deneyelim.  
  
## <a name="what-was-the-app-doing"></a>Uygulama ne yapıyor?  
 İlk nottaki şey, yığının tabanında `async` anahtar sözcük makinelerdir.  Bir `async` yöntemde uygulamanın gerçekten ne yaptığını belirlemek soruna neden olabilir. yığın, kaynak çağrının bağlamını kaybettiğinden ve `async` kodu farklı bir iş parçacığında çalıştırmıştır. Bununla birlikte, uygulamanın ilk sayfasını yüklemeye çalıştığı anlaşıyoruz.  Uygulamasında `NavigationArgs.Setup`, aşağıdaki kod erişim ihlaline neden oldu:  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 Bu örnekte, `LayoutVM` `AppViewModel.Current` özelliği **null**idi.  Bazı meta veri yokluğu, hafif davranış farkına neden oldu ve uygulamanın beklendiği gibi küme yerine başlatılmamış bir özellik ile sonuçlandı.  Kodda başlatılmış olması `LayoutVM` gereken bir kesme noktası ayarlamak durumunda ışık oluşturabilir.  Ancak, türünün olduğunu `LayoutVM` `App.Core.ViewModels.Layout.LayoutApplicationVM`unutmayın.  Şu ana kadar Rd. xml dosyasında olan tek metaveri yönergesi şu şekilde bulunur:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Hata `App.Core.ViewModels.Layout.LayoutApplicationVM` için olası bir aday, farklı bir ad alanında olduğu için meta veriler eksik.  
  
 Bu durumda, sorunu `App.Core.ViewModels` çözen bir çalışma zamanı yönergesi ekleme. Kök neden, <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> **null**döndüren yöntemine yönelik bir API çağrısıdır ve uygulama kilitlenme gerçekleşene kadar sorunu sessizce yok sayılır.  
  
 Dinamik programlamada, .NET Native altında yansıma API 'leri kullanırken iyi bir uygulama hata durumunda özel durum oluşturan <xref:System.Type.GetType%2A?displayProperty=nameWithType> aşırı yüklemeleri kullanmaktır.  
  
## <a name="is-this-an-isolated-case"></a>Bu yalıtılmış bir durumdur mi?  
 Kullanırken `App.Core.ViewModels`diğer sorunlar da oluşabilir.  Eksik bir meta veri özel durumunun belirlenmesi ve düzeltilmesi ya da zaman tasarrufu ve daha büyük bir tür sınıfı için yönergeler eklenmesi gerektiğine karar vermelisiniz.  Burada, çıkış `dynamic` ikilisinin `App.Core.ViewModels` elde edilen boyut artışı bir sorun değilse, için meta verileri eklemek en iyi yaklaşım olabilir.  
  
## <a name="could-the-code-be-rewritten"></a>Kod yeniden yazılabilir mi?  
 Uygulamanın `typeof(LayoutApplicationVM)` `browse` yerine kullanıldıysa, araç zinciri korunan meta verileri olabilir. `Type.GetType("LayoutApplicationVM")`  Ancak, tür örneği oluşturulurken `invoke` [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durumuna yol gösteren meta verileri hala oluşturmazdı. Özel durumu engellemek için, ad alanı veya `dynamic` ilkeyi belirten tür için bir çalışma zamanı yönergesi eklemeniz gerekir. Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Örnek: Verileri bağlarken özel durumları işleme](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
