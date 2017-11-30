---
title: "Örnek: Dinamik Programlama Sorunlarını Giderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de808e333506858d6591dab6c7c06e6a3e9ddabd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="d1451-102">Örnek: Dinamik Programlama Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="d1451-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="d1451-103">Bu konu, .NET yerel geliştirici yayın öncesi yazılımı olan Önizleme, ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d1451-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="d1451-104">Önizlemesi'nden indirebilirsiniz [Microsoft Connect Web](http://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerektirir).</span><span class="sxs-lookup"><span data-stu-id="d1451-104">You can download the preview from the [Microsoft Connect website](http://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="d1451-105">Tüm meta veri arama hataları kullanılarak geliştirilen uygulamalardaki [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı bir özel durum zinciri sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d1451-105">Not all metadata lookup failures in apps developed using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain result in an exception.</span></span>  <span data-ttu-id="d1451-106">Bazı uygulama öngörülemeyen şekillerde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1451-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="d1451-107">Aşağıdaki örnek, null bir nesne başvurarak neden bir erişim ihlali gösterir:</span><span class="sxs-lookup"><span data-stu-id="d1451-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="d1451-108">Bu özel durum "El ile eksik meta veri çözümleme" bölümünde açıklanan üç adımı yaklaşım kullanarak sorun gidermek deneyelim [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="d1451-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="d1451-109">Uygulama yaptıklarını edildi?</span><span class="sxs-lookup"><span data-stu-id="d1451-109">What was the app doing?</span></span>  
 <span data-ttu-id="d1451-110">Dikkat edilecek ilk şey `async` yığınının tabanında anahtar sözcüğü makineler.</span><span class="sxs-lookup"><span data-stu-id="d1451-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="d1451-111">Hangi uygulamanın gerçekten yapmakta olduğu belirleme bir `async` yöntemi olabilir sorunlu, çünkü yığın kaynak çağrı bağlamında kaybetti ve çalıştırıldı `async` kodu farklı bir iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d1451-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="d1451-112">Ancak, biz uygulamayı ilk sayfa yükleme çalışıyor türetme.</span><span class="sxs-lookup"><span data-stu-id="d1451-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="d1451-113">Uygulamasında için `NavigationArgs.Setup`, aşağıdaki kodu erişim ihlali neden:</span><span class="sxs-lookup"><span data-stu-id="d1451-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="d1451-114">Bu örnekte `LayoutVM` özelliği `AppViewModel.Current` olan **null**.</span><span class="sxs-lookup"><span data-stu-id="d1451-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="d1451-115">Meta veri bazı yokluğu Zarif davranışı fark neden ve bir özellik kümesi yerine beklenen uygulama olarak başlatılmadı ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="d1451-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="d1451-116">Kodda kesme noktası ayarlama nerede `LayoutVM` başlatılmamış ışık durumunuza throw.</span><span class="sxs-lookup"><span data-stu-id="d1451-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="d1451-117">Ancak, dikkat edin `LayoutVM`'s türü `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="d1451-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="d1451-118">Şu ana kadar rd.xml dosyasında bulunan yalnızca meta veri yönergesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="d1451-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="d1451-119">Hatanın olası bir aday olan `App.Core.ViewModels.Layout.LayoutApplicationVM` farklı bir ad alanında olduğundan meta veriler eksik.</span><span class="sxs-lookup"><span data-stu-id="d1451-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="d1451-120">Bu durumda, bir çalışma zamanı yönerge için ekleme `App.Core.ViewModels` sorunu Çözümlendi.</span><span class="sxs-lookup"><span data-stu-id="d1451-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="d1451-121">Bir API çağrısı için kök nedeni <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> döndürülen yöntemi **null**, ve bir kilitlenme oluştu dek uygulama sessizce sorun yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="d1451-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="d1451-122">Dinamik programlama, yansıma API'leri kullanırken iyi bir uygulama içinde altında [!INCLUDE[net_native](../../../includes/net-native-md.md)] kullanmaktır <xref:System.Type.GetType%2A?displayProperty=nameWithType> hatasında bir özel durum aşırı.</span><span class="sxs-lookup"><span data-stu-id="d1451-122">In dynamic programming, a good practice when using reflection APIs under [!INCLUDE[net_native](../../../includes/net-native-md.md)] is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="d1451-123">Bu yalıtılmış bir durumdur?</span><span class="sxs-lookup"><span data-stu-id="d1451-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="d1451-124">Diğer sorunlar da kullanırken doğabilecek `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="d1451-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="d1451-125">Tanımlama ve eksik her meta veri özel durum düzelttikten veya zaman kazandırır ve daha büyük bir sınıf türleri için yönergeleri ekleme değer olup olmadığını karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1451-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="d1451-126">Burada, ekleme `dynamic` meta verilerini `App.Core.ViewModels` elde edilen boyutu artışı çıkış ikili bir sorun yoksa en iyi yaklaşım olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1451-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="d1451-127">Kodu yeniden yazılmıştır?</span><span class="sxs-lookup"><span data-stu-id="d1451-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="d1451-128">Uygulamayı kullandıysa `typeof(LayoutApplicationVM)` yerine `Type.GetType("LayoutApplicationVM")`, araç zinciri muhafaza edilmesini `browse` meta verileri.</span><span class="sxs-lookup"><span data-stu-id="d1451-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="d1451-129">Ancak, yine oluşturduktan olmayacaktır `invoke` neden için meta verileri bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) türü örneği oluşturulurken özel durum.</span><span class="sxs-lookup"><span data-stu-id="d1451-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="d1451-130">Özel durum önlemek için hala bir çalışma zamanı yönerge ad alanı veya belirten türü eklemek olurdu `dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="d1451-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="d1451-131">Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="d1451-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1451-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1451-132">See Also</span></span>  
 [<span data-ttu-id="d1451-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="d1451-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="d1451-134">Örnek: Veri bağlama sırasında özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="d1451-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
