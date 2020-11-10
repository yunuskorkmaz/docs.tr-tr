---
ms.openlocfilehash: c090e99cd0569a843a4c505ad11b8da5740213e8
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440485"
---
### <a name="blazor-updated-validation-logic-for-static-web-assets"></a><span data-ttu-id="6e841-101">Blazor: statik Web varlıkları için doğrulama mantığı güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="6e841-101">Blazor: Updated validation logic for static web assets</span></span>

<span data-ttu-id="6e841-102">ASP.NET Core 3,1 ve Blazor WebAssembly 3,2 ' de statik Web varlıkları için çakışma doğrulamasında bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="6e841-102">There was an issue in conflict validation for static web assets in ASP.NET Core 3.1 and Blazor WebAssembly 3.2.</span></span> <span data-ttu-id="6e841-103">Sorun:</span><span class="sxs-lookup"><span data-stu-id="6e841-103">The issue:</span></span>

* <span data-ttu-id="6e841-104">Razor sınıf kitaplıkları (RCLs) ve Blazor WebAssembly uygulamalarından gelen konak varlıkları ve varlıklar arasında doğru çakışma algılamayı engelledi.</span><span class="sxs-lookup"><span data-stu-id="6e841-104">Prevented proper conflict detection between the host assets and assets from Razor Class Libraries (RCLs) and Blazor WebAssembly apps.</span></span>
* <span data-ttu-id="6e841-105">, Varsayılan olarak, RCLs içindeki statik web varlıklarının ön ek kapsamında sunulduğundan, genellikle Blazor WebAssembly uygulamalarını etkiler `_content/$(PackageId)` .</span><span class="sxs-lookup"><span data-stu-id="6e841-105">Mostly affects Blazor WebAssembly apps, since by default, static web assets in RCLs are served under the `_content/$(PackageId)` prefix.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6e841-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6e841-106">Version introduced</span></span>

<span data-ttu-id="6e841-107">5.0</span><span class="sxs-lookup"><span data-stu-id="6e841-107">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6e841-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="6e841-108">Old behavior</span></span>

<span data-ttu-id="6e841-109">Geliştirme sırasında, bir RCL 'nin statik web varlıklarının aynı konak yolu ana bilgisayar proje varlıkları ile sessizce geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="6e841-109">During development, an RCL's static web assets could be silently overridden with host project assets on the same host path.</span></span> <span data-ttu-id="6e841-110">*/Folder/file.txt* adresinden sunulacak statik bir web varlığı tanımlamış bir RCL düşünün.</span><span class="sxs-lookup"><span data-stu-id="6e841-110">Consider an RCL that has defined a static web asset to be served at */folder/file.txt*.</span></span> <span data-ttu-id="6e841-111">Ana bilgisayar *Wwwroot/klasör/file.txt* ' a bir dosya yerleştirirse, sunucudaki dosya, RCL veya Blazor WebAssembly uygulamasındaki dosyayı sessizce yok kılar.</span><span class="sxs-lookup"><span data-stu-id="6e841-111">If the host placed a file at *wwwroot/folder/file.txt* , the file on the server silently overrode the file on the RCL or Blazor WebAssembly app.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6e841-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="6e841-112">New behavior</span></span>

<span data-ttu-id="6e841-113">ASP.NET Core, bu sorunun ne zaman gerçekleştiğini doğru şekilde algılar.</span><span class="sxs-lookup"><span data-stu-id="6e841-113">ASP.NET Core correctly detects when this issue happens.</span></span> <span data-ttu-id="6e841-114">İlgili eylemi gerçekleştirebileceğiniz için, çakışmayı kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="6e841-114">It informs you, the user, of the conflict so that you can take the appropriate action.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6e841-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="6e841-115">Reason for change</span></span>

<span data-ttu-id="6e841-116">Statik web varlıklarının, projenin *Wwwroot* ana bilgisayarındaki dosyalar tarafından geçersiz kılınabilir olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="6e841-116">Static web assets weren't intended to be overridable by files on the *wwwroot* host of the project.</span></span> <span data-ttu-id="6e841-117">Bu dosyaların geçersiz kılınmasına izin verilmesi, tanılanması zor hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e841-117">Allowing for the overriding of those files could lead to errors that are difficult to diagnose.</span></span> <span data-ttu-id="6e841-118">Sonuç, yayımlanan uygulamalarda tanımsız davranış değişiklikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e841-118">The result could be undefined behavior changes in published apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6e841-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6e841-119">Recommended action</span></span>

<span data-ttu-id="6e841-120">Varsayılan olarak, bir RCL dosyasının konaktaki bir dosyayla çakışmasının nedeni yoktur.</span><span class="sxs-lookup"><span data-stu-id="6e841-120">By default, there's no reason for an RCL file to conflict with a file on the host.</span></span> <span data-ttu-id="6e841-121">RCL dosyaları ön ekine sahiptir `_content/${PackageId}` .</span><span class="sxs-lookup"><span data-stu-id="6e841-121">RCL files are prefixed with `_content/${PackageId}`.</span></span> <span data-ttu-id="6e841-122">Blazor WebAssembly dosyaları, çakışma daha kolay hale getiren ana bilgisayar URL 'SI alanının köküne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6e841-122">Blazor WebAssembly files are placed at the root of the host URL space, which makes conflicts easier.</span></span> <span data-ttu-id="6e841-123">Örneğin, Blazor WebAssembly Apps, konağın *Wwwroot* klasörüne de dahil olabileceği bir *tercih edilen Icon. ico* dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="6e841-123">For example, Blazor WebAssembly apps contain a *favicon.ico* file that the host might also include in its *wwwroot* folder.</span></span>

<span data-ttu-id="6e841-124">Çakışmanın kaynağı bir RCL dosyası ise, genellikle kodun varlıkları kitaplıktan projenin *Wwwroot* klasörüne kopyalandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e841-124">If the conflict's source is an RCL file, it often means code is copying assets from the library into the project's *wwwroot* folder.</span></span> <span data-ttu-id="6e841-125">Dosyaları kopyalamak için kod yazma, statik web varlıklarının birincil hedefini erteler.</span><span class="sxs-lookup"><span data-stu-id="6e841-125">Writing code to copy files defeats a primary goal of static web assets.</span></span> <span data-ttu-id="6e841-126">Bu hedef, içerik yeni bir derleme tetiklemeye gerek kalmadan güncelleştirildiğinde tarayıcıda güncelleştirmeleri almak için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6e841-126">This goal is fundamental to get updates on the browser when the contents are updated without having to trigger a new compilation.</span></span>

<span data-ttu-id="6e841-127">Bu davranışı korumayı ve dosyayı konakta korumayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e841-127">You may choose to preserve this behavior and maintain the file on the host.</span></span> <span data-ttu-id="6e841-128">Bunu yapmak için, dosyayı özel bir MSBuild hedefi olan statik Web varlıkları listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6e841-128">To do so, remove the file from the list of static web assets with a custom MSBuild target.</span></span>

<span data-ttu-id="6e841-129">Ana bilgisayar projesinin dosyası yerine RCL 'nin dosyasını veya Blazor WebAssembly uygulamasının dosyasını kullanmak için, dosyayı konak projesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6e841-129">To use the RCL's file or the Blazor WebAssembly app's file instead of the host project's file, remove the file from the host project.</span></span>

#### <a name="category"></a><span data-ttu-id="6e841-130">Kategori</span><span class="sxs-lookup"><span data-stu-id="6e841-130">Category</span></span>

<span data-ttu-id="6e841-131">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6e841-131">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6e841-132">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6e841-132">Affected APIs</span></span>

<span data-ttu-id="6e841-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6e841-133">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
