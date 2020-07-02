---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614898"
---
### <a name="wpf-pointer-based-touch-stack"></a><span data-ttu-id="91059-101">WPF Işaretçi tabanlı dokunmatik yığın</span><span class="sxs-lookup"><span data-stu-id="91059-101">WPF Pointer-Based Touch Stack</span></span>

#### <a name="details"></a><span data-ttu-id="91059-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="91059-102">Details</span></span>

<span data-ttu-id="91059-103">Bu değişiklik, isteğe bağlı WM_POINTER tabanlı WPF dokunmatik/Stilus yığınını etkinleştirme özelliği ekler.</span><span class="sxs-lookup"><span data-stu-id="91059-103">This change adds the ability to enable an optional WM_POINTER based WPF touch/stylus stack.</span></span>  <span data-ttu-id="91059-104">Bunu açıkça etkinleştirmesiz geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmez. İsteğe bağlı WM_POINTER tabanlı dokunma/ekran kalemi yığınında bilinen geçerli sorunlar:</span><span class="sxs-lookup"><span data-stu-id="91059-104">Developers that do not explicitly enable this should see no change in WPF touch/stylus behavior.Current Known Issues With optional WM_POINTER based touch/stylus stack:</span></span>

- <span data-ttu-id="91059-105">Gerçek zamanlı mürekkep oluşturma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="91059-105">No support for real-time inking.</span></span>
- <span data-ttu-id="91059-106">Mürekkep oluşturma ve StylusPlugIns çalışmaya devam ederken, Kullanıcı arabirimi Iş parçacığında işlenecektir ve bu da kötü performansa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="91059-106">While inking and StylusPlugins will still work, they will be processed on the UI Thread which can lead to poor performance.</span></span>
- <span data-ttu-id="91059-107">Dokunmatik/ekran kalemi olaylarından fare olaylarına yükseltme yapılan değişiklikler nedeniyle davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="91059-107">Behavioral changes due to changes in promotion from touch/stylus events to mouse events</span></span>
- <span data-ttu-id="91059-108">Düzenleme farklı davranabilirler</span><span class="sxs-lookup"><span data-stu-id="91059-108">Manipulation may behave differently</span></span>
- <span data-ttu-id="91059-109">Sürükle/bırak, dokunma girişi için uygun geri bildirimi göstermez</span><span class="sxs-lookup"><span data-stu-id="91059-109">Drag/Drop will not show appropriate feedback for touch input</span></span>
- <span data-ttu-id="91059-110">Bu, ekran kalemi girişini etkilemez</span><span class="sxs-lookup"><span data-stu-id="91059-110">This does not affect stylus input</span></span>
- <span data-ttu-id="91059-111">Sürükle/bırak, artık dokunmatik/ekran kalemi olaylarında başlatılamaz</span><span class="sxs-lookup"><span data-stu-id="91059-111">Drag/Drop can no longer be initiated on touch/stylus events</span></span>
- <span data-ttu-id="91059-112">Bu, fare girişi algılanana kadar uygulamanın askıda kalmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="91059-112">This can potentially hang the application until mouse input is detected.</span></span>
- <span data-ttu-id="91059-113">Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak işlemini başlatmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91059-113">Instead, developers should initiate drag and drop from mouse events.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="91059-114">Öneri</span><span class="sxs-lookup"><span data-stu-id="91059-114">Suggestion</span></span>

<span data-ttu-id="91059-115">Bu yığını etkinleştirmek isteyen geliştiriciler, uygulamanın App.config dosyasına aşağıdakileri ekleyebilir/birleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="91059-115">Developers who wish to enable this stack can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="91059-116">Bu değer kaldırıldığında veya false olarak ayarlandığında, bu isteğe bağlı yığın kapanır. Bu yığının yalnızca Windows 10 Creators Update ve üzeri sürümlerde kullanılabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="91059-116">Removing this or setting the value to false will turn this optional stack off.Note that this stack is available only on Windows 10 Creators Update and above.</span></span>

| <span data-ttu-id="91059-117">Name</span><span class="sxs-lookup"><span data-stu-id="91059-117">Name</span></span>    | <span data-ttu-id="91059-118">Değer</span><span class="sxs-lookup"><span data-stu-id="91059-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="91059-119">Kapsam</span><span class="sxs-lookup"><span data-stu-id="91059-119">Scope</span></span>   | <span data-ttu-id="91059-120">Edge</span><span class="sxs-lookup"><span data-stu-id="91059-120">Edge</span></span>        |
| <span data-ttu-id="91059-121">Sürüm</span><span class="sxs-lookup"><span data-stu-id="91059-121">Version</span></span> | <span data-ttu-id="91059-122">4,7</span><span class="sxs-lookup"><span data-stu-id="91059-122">4.7</span></span>         |
| <span data-ttu-id="91059-123">Tür</span><span class="sxs-lookup"><span data-stu-id="91059-123">Type</span></span>    | <span data-ttu-id="91059-124">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="91059-124">Retargeting</span></span> |
