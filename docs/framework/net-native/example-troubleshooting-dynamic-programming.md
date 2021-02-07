---
description: 'Daha fazla bilgi: örnek: dinamik programlama sorunlarını giderme'
title: 'Örnek: Dinamik Programlama Sorunlarını Giderme'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: 7ad3fde9c81800123abe899e2f696c3833fed5bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747861"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="5c5a4-103">Örnek: Dinamik Programlama Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="5c5a4-103">Example: Troubleshooting Dynamic Programming</span></span>

> [!NOTE]
> <span data-ttu-id="5c5a4-104">Bu konu, yayın öncesi yazılım olan .NET Native geliştirici önizlemesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-104">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="5c5a4-105">Önizlemeyi [Microsoft Connect Web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerekir).</span><span class="sxs-lookup"><span data-stu-id="5c5a4-105">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="5c5a4-106">.NET Native araç zinciri kullanılarak geliştirilen uygulamalardaki tüm meta veri arama hatalarının bir özel durum sonucu yoktur.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-106">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="5c5a4-107">Bazıları, bir uygulamada öngörülemeyen yollarla bildirimde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-107">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="5c5a4-108">Aşağıdaki örnek, null bir nesneye başvuruda bulunarak oluşan bir erişim ihlali gösterir:</span><span class="sxs-lookup"><span data-stu-id="5c5a4-108">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="5c5a4-109">[Kullanmaya](getting-started-with-net-native.md)başlama konusunun "eksik meta verileri el ile çözümleme" bölümünde özetlenen üç adımlı yaklaşımı kullanarak bu özel durumu gidermeye deneyelim.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-109">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="5c5a4-110">Uygulama ne yapıyordu?</span><span class="sxs-lookup"><span data-stu-id="5c5a4-110">What was the app doing?</span></span>  

 <span data-ttu-id="5c5a4-111">İlk nottaki şey, `async` yığının tabanında anahtar sözcük makinelerdir.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-111">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="5c5a4-112">Bir yöntemde uygulamanın gerçekten ne yaptığını belirlemek soruna neden olabilir `async` . yığın, kaynak çağrının bağlamını kaybettiğinden ve `async` kodu farklı bir iş parçacığında çalıştırmıştır.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-112">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="5c5a4-113">Bununla birlikte, uygulamanın ilk sayfasını yüklemeye çalıştığı anlaşıyoruz.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-113">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="5c5a4-114">Uygulamasında `NavigationArgs.Setup` , aşağıdaki kod erişim ihlaline neden oldu:</span><span class="sxs-lookup"><span data-stu-id="5c5a4-114">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="5c5a4-115">Bu örnekte, `LayoutVM` özelliği `AppViewModel.Current` **null** idi.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-115">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="5c5a4-116">Bazı meta veri yokluğu, hafif davranış farkına neden oldu ve uygulamanın beklendiği gibi küme yerine başlatılmamış bir özellik ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-116">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="5c5a4-117">Kodda başlatılmış olması gereken bir kesme noktası ayarlamak `LayoutVM` durumunda ışık oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-117">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="5c5a4-118">Ancak, `LayoutVM` türünün olduğunu unutmayın `App.Core.ViewModels.Layout.LayoutApplicationVM` .</span><span class="sxs-lookup"><span data-stu-id="5c5a4-118">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="5c5a4-119">rd.xml dosyasında şu ana kadar tek metaveri yönergesi bulunur:</span><span class="sxs-lookup"><span data-stu-id="5c5a4-119">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="5c5a4-120">Hata için olası bir aday, `App.Core.ViewModels.Layout.LayoutApplicationVM` farklı bir ad alanında olduğu için meta veriler eksik.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-120">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="5c5a4-121">Bu durumda, sorunu çözen bir çalışma zamanı yönergesi ekleme `App.Core.ViewModels` .</span><span class="sxs-lookup"><span data-stu-id="5c5a4-121">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="5c5a4-122">Kök neden, null döndüren yöntemine yönelik bir API çağrısıdır <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> ve uygulama kilitlenme gerçekleşene kadar sorunu sessizce yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-122">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="5c5a4-123">Dinamik programlamada, .NET Native altında yansıma API 'Leri kullanırken iyi bir uygulama <xref:System.Type.GetType%2A?displayProperty=nameWithType> hata durumunda özel durum oluşturan aşırı yüklemeleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-123">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="5c5a4-124">Bu yalıtılmış bir durumdur mi?</span><span class="sxs-lookup"><span data-stu-id="5c5a4-124">Is this an isolated case?</span></span>  

 <span data-ttu-id="5c5a4-125">Kullanırken diğer sorunlar da oluşabilir `App.Core.ViewModels` .</span><span class="sxs-lookup"><span data-stu-id="5c5a4-125">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="5c5a4-126">Eksik bir meta veri özel durumunun belirlenmesi ve düzeltilmesi ya da zaman tasarrufu ve daha büyük bir tür sınıfı için yönergeler eklenmesi gerektiğine karar vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-126">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="5c5a4-127">Burada, `dynamic` `App.Core.ViewModels` Çıkış ikilisinin elde edilen boyut artışı bir sorun değilse, için meta verileri eklemek en iyi yaklaşım olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-127">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="5c5a4-128">Kod yeniden yazılabilir mi?</span><span class="sxs-lookup"><span data-stu-id="5c5a4-128">Could the code be rewritten?</span></span>  

 <span data-ttu-id="5c5a4-129">Uygulamanın `typeof(LayoutApplicationVM)` yerine kullanıldıysa `Type.GetType("LayoutApplicationVM")` , araç zinciri korunan `browse` meta verileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-129">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="5c5a4-130">Ancak, `invoke` tür örneği oluşturulurken [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumuna yol gösteren meta verileri hala oluşturmazdı.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-130">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="5c5a4-131">Özel durumu engellemek için, ad alanı veya ilkeyi belirten tür için bir çalışma zamanı yönergesi eklemeniz gerekir `dynamic` .</span><span class="sxs-lookup"><span data-stu-id="5c5a4-131">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="5c5a4-132">Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="5c5a4-132">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5a4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c5a4-133">See also</span></span>

- [<span data-ttu-id="5c5a4-134">Başlarken</span><span class="sxs-lookup"><span data-stu-id="5c5a4-134">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="5c5a4-135">Örnek: Veri Bağlama Sırasında Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="5c5a4-135">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)
