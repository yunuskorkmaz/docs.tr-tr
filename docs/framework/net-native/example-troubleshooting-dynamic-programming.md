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
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="604ff-102">Örnek: Dinamik Programlama Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="604ff-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="604ff-103">Bu konuda, .NET Native Geliştirici yayın öncesi bir yazılım olan Önizleme, ifade eder.</span><span class="sxs-lookup"><span data-stu-id="604ff-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="604ff-104">Önizlemesi'nden indirebileceğiniz [Microsoft Connect Web sitesi](https://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerekir).</span><span class="sxs-lookup"><span data-stu-id="604ff-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="604ff-105">Tüm meta veri arama hataları kullanılarak geliştirilen uygulamalarda [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı bir özel durum zinciri sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="604ff-105">Not all metadata lookup failures in apps developed using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain result in an exception.</span></span>  <span data-ttu-id="604ff-106">Bazı uygulama beklenmedik bir şekilde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="604ff-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="604ff-107">Aşağıdaki örnek, bir null Nesne başvurarak neden bir erişim ihlali gösterir:</span><span class="sxs-lookup"><span data-stu-id="604ff-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="604ff-108">Deneyelim "Meta veriler eksik elle Çözümle" bölümünde belirtilen üç adımlı yaklaşım kullanarak bu özel durum sorunlarını giderme [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="604ff-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="604ff-109">Uygulama neler oldu?</span><span class="sxs-lookup"><span data-stu-id="604ff-109">What was the app doing?</span></span>  
 <span data-ttu-id="604ff-110">Dikkat edilecek ilk şey `async` temel yığın anahtar sözcüğü makineler.</span><span class="sxs-lookup"><span data-stu-id="604ff-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="604ff-111">Hangi uygulamayı gerçekten yapmakta olduğu belirleyen bir `async` yöntemi olabilir sorunlu, çünkü yığın kaynak çağrı bağlamında kesildi ve çalıştırıldı `async` farklı bir iş parçacığında kod.</span><span class="sxs-lookup"><span data-stu-id="604ff-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="604ff-112">Ancak, uygulama, ilk sayfa çalışıyor çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="604ff-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="604ff-113">İçin uygulamada `NavigationArgs.Setup`, aşağıdaki kod erişim ihlaline neden oldu:</span><span class="sxs-lookup"><span data-stu-id="604ff-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="604ff-114">Bu örnekte, `LayoutVM` özelliği `AppViewModel.Current` olduğu **null**.</span><span class="sxs-lookup"><span data-stu-id="604ff-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="604ff-115">Meta verileri bazı olmaması, hafif bir davranışı fark neden ve yerine küme, beklenen uygulaması olarak başlatılmamış bir özellikte sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="604ff-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="604ff-116">Kodda bir kesme noktası ayarlama burada `LayoutVM` başlatılmamış ışık durumunuza fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="604ff-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="604ff-117">Ancak, unutmayın `LayoutVM`ın türü `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="604ff-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="604ff-118">Şu ana kadar rd.xml dosyasında mevcut yalnızca meta veri yönergesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="604ff-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="604ff-119">Hatanın olası bir aday olan `App.Core.ViewModels.Layout.LayoutApplicationVM` farklı bir ad alanında olduğundan meta veriler eksik.</span><span class="sxs-lookup"><span data-stu-id="604ff-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="604ff-120">Bu durumda, bir çalışma zamanı yönerge için ekleme `App.Core.ViewModels` sorun çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="604ff-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="604ff-121">Bir API çağrısı için kök nedeni <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> döndürülen yöntemi **null**, ve bir kilitlenme oluştu kadar uygulamayı sessiz bir şekilde sorun yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="604ff-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="604ff-122">Dinamik programlama, yansıma API'leri kullanırken iyi bir uygulama içinde altında [!INCLUDE[net_native](../../../includes/net-native-md.md)] kullanmaktır <xref:System.Type.GetType%2A?displayProperty=nameWithType> hatasında bir özel durum aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="604ff-122">In dynamic programming, a good practice when using reflection APIs under [!INCLUDE[net_native](../../../includes/net-native-md.md)] is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="604ff-123">Bu, yalıtılmış bir durum mu?</span><span class="sxs-lookup"><span data-stu-id="604ff-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="604ff-124">Diğer sorunları da kullanırken ortaya çıkabilir `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="604ff-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="604ff-125">Tanımlama ve eksik her meta veri özel durum düzeltme veya zaman tasarrufu sağlamanıza ve ekleme yönergeleri daha büyük bir sınıf türü için değer olup olmadığını karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="604ff-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="604ff-126">Burada, ekleme `dynamic` meta verilerini `App.Core.ViewModels` en iyi yaklaşım, sonuçta elde edilen boyutunu artırma çıkış ikili bir sorun yoksa olabilir.</span><span class="sxs-lookup"><span data-stu-id="604ff-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="604ff-127">Kod yazılması?</span><span class="sxs-lookup"><span data-stu-id="604ff-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="604ff-128">Uygulama kullanmışsınız `typeof(LayoutApplicationVM)` yerine `Type.GetType("LayoutApplicationVM")`, araç zincirinizi korunur `browse` meta verileri.</span><span class="sxs-lookup"><span data-stu-id="604ff-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="604ff-129">Ancak, yine de oluşturduktan mıydı `invoke` neden için meta verileri bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) türü örneği oluşturulurken özel durum.</span><span class="sxs-lookup"><span data-stu-id="604ff-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="604ff-130">Özel durum önlemek için yine de ad alanı veya belirten türü için bir çalışma zamanı yönerge eklemeniz gerekir `dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="604ff-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="604ff-131">Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="604ff-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604ff-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="604ff-132">See Also</span></span>  
 [<span data-ttu-id="604ff-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="604ff-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="604ff-134">Örnek: Veri Bağlama Sırasında Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="604ff-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
