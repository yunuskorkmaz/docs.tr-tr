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
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="81e77-102">Örnek: Dinamik Programlama Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="81e77-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
> <span data-ttu-id="81e77-103">Bu konu, yayın öncesi yazılım olan .NET Native geliştirici önizlemesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="81e77-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="81e77-104">Önizlemeyi [Microsoft Connect Web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerekir).</span><span class="sxs-lookup"><span data-stu-id="81e77-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="81e77-105">.NET Native araç zinciri kullanılarak geliştirilen uygulamalardaki tüm meta veri arama hatalarının bir özel durum sonucu yoktur.</span><span class="sxs-lookup"><span data-stu-id="81e77-105">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="81e77-106">Bazıları, bir uygulamada öngörülemeyen yollarla bildirimde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="81e77-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="81e77-107">Aşağıdaki örnek, null bir nesneye başvuruda bulunarak oluşan bir erişim ihlali gösterir:</span><span class="sxs-lookup"><span data-stu-id="81e77-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="81e77-108">[Kullanmaya](../../../docs/framework/net-native/getting-started-with-net-native.md)başlama konusunun "eksik meta verileri el ile çözümleme" bölümünde özetlenen üç adımlı yaklaşımı kullanarak bu özel durumu gidermeye deneyelim.</span><span class="sxs-lookup"><span data-stu-id="81e77-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="81e77-109">Uygulama ne yapıyor?</span><span class="sxs-lookup"><span data-stu-id="81e77-109">What was the app doing?</span></span>  
 <span data-ttu-id="81e77-110">İlk nottaki şey, yığının tabanında `async` anahtar sözcük makinelerdir.</span><span class="sxs-lookup"><span data-stu-id="81e77-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="81e77-111">Bir `async` yöntemde uygulamanın gerçekten ne yaptığını belirlemek soruna neden olabilir. yığın, kaynak çağrının bağlamını kaybettiğinden ve `async` kodu farklı bir iş parçacığında çalıştırmıştır.</span><span class="sxs-lookup"><span data-stu-id="81e77-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="81e77-112">Bununla birlikte, uygulamanın ilk sayfasını yüklemeye çalıştığı anlaşıyoruz.</span><span class="sxs-lookup"><span data-stu-id="81e77-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="81e77-113">Uygulamasında `NavigationArgs.Setup`, aşağıdaki kod erişim ihlaline neden oldu:</span><span class="sxs-lookup"><span data-stu-id="81e77-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="81e77-114">Bu örnekte, `LayoutVM` `AppViewModel.Current` özelliği **null**idi.</span><span class="sxs-lookup"><span data-stu-id="81e77-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="81e77-115">Bazı meta veri yokluğu, hafif davranış farkına neden oldu ve uygulamanın beklendiği gibi küme yerine başlatılmamış bir özellik ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="81e77-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="81e77-116">Kodda başlatılmış olması `LayoutVM` gereken bir kesme noktası ayarlamak durumunda ışık oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="81e77-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="81e77-117">Ancak, türünün olduğunu `LayoutVM` `App.Core.ViewModels.Layout.LayoutApplicationVM`unutmayın.</span><span class="sxs-lookup"><span data-stu-id="81e77-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="81e77-118">Şu ana kadar Rd. xml dosyasında olan tek metaveri yönergesi şu şekilde bulunur:</span><span class="sxs-lookup"><span data-stu-id="81e77-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="81e77-119">Hata `App.Core.ViewModels.Layout.LayoutApplicationVM` için olası bir aday, farklı bir ad alanında olduğu için meta veriler eksik.</span><span class="sxs-lookup"><span data-stu-id="81e77-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="81e77-120">Bu durumda, sorunu `App.Core.ViewModels` çözen bir çalışma zamanı yönergesi ekleme.</span><span class="sxs-lookup"><span data-stu-id="81e77-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="81e77-121">Kök neden, <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> **null**döndüren yöntemine yönelik bir API çağrısıdır ve uygulama kilitlenme gerçekleşene kadar sorunu sessizce yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="81e77-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="81e77-122">Dinamik programlamada, .NET Native altında yansıma API 'leri kullanırken iyi bir uygulama hata durumunda özel durum oluşturan <xref:System.Type.GetType%2A?displayProperty=nameWithType> aşırı yüklemeleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="81e77-122">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="81e77-123">Bu yalıtılmış bir durumdur mi?</span><span class="sxs-lookup"><span data-stu-id="81e77-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="81e77-124">Kullanırken `App.Core.ViewModels`diğer sorunlar da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="81e77-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="81e77-125">Eksik bir meta veri özel durumunun belirlenmesi ve düzeltilmesi ya da zaman tasarrufu ve daha büyük bir tür sınıfı için yönergeler eklenmesi gerektiğine karar vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="81e77-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="81e77-126">Burada, çıkış `dynamic` ikilisinin `App.Core.ViewModels` elde edilen boyut artışı bir sorun değilse, için meta verileri eklemek en iyi yaklaşım olabilir.</span><span class="sxs-lookup"><span data-stu-id="81e77-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="81e77-127">Kod yeniden yazılabilir mi?</span><span class="sxs-lookup"><span data-stu-id="81e77-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="81e77-128">Uygulamanın `typeof(LayoutApplicationVM)` `browse` yerine kullanıldıysa, araç zinciri korunan meta verileri olabilir. `Type.GetType("LayoutApplicationVM")`</span><span class="sxs-lookup"><span data-stu-id="81e77-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="81e77-129">Ancak, tür örneği oluşturulurken `invoke` [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durumuna yol gösteren meta verileri hala oluşturmazdı.</span><span class="sxs-lookup"><span data-stu-id="81e77-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="81e77-130">Özel durumu engellemek için, ad alanı veya `dynamic` ilkeyi belirten tür için bir çalışma zamanı yönergesi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="81e77-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="81e77-131">Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="81e77-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e77-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81e77-132">See also</span></span>

- [<span data-ttu-id="81e77-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="81e77-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="81e77-134">Örnek: Verileri bağlarken özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="81e77-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
