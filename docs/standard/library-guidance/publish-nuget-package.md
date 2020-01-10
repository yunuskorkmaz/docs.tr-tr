---
title: NuGet paketi yayımlama
description: NuGet 'e .NET kitaplıklarını yayımlamaya yönelik en iyi yöntem önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: e567fe3f7e00bf322cdd50786e50128961107469
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706471"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="00cdd-103">NuGet paketi yayımlama</span><span class="sxs-lookup"><span data-stu-id="00cdd-103">Publishing a NuGet package</span></span>

<span data-ttu-id="00cdd-104">NuGet paketleri, paket depolarından yayımlanır ve kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00cdd-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="00cdd-105">NuGet.org, en yaygın olarak bilinen ve kullanılan depoken, NuGet paketlerini yayımlamak için birçok yer vardır:</span><span class="sxs-lookup"><span data-stu-id="00cdd-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="00cdd-106">**[NuGet.org](https://www.nuget.org/)** , NuGet paketleri için birincil çevrimiçi depodur.</span><span class="sxs-lookup"><span data-stu-id="00cdd-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="00cdd-107">NuGet.org üzerindeki tüm paketler herkese açık olarak herkes tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="00cdd-108">Varsayılan olarak, Visual Studio 'nun bir paket kaynağı olarak NuGet.org vardır ve birçok geliştirici NuGet.org, etkileşime gitireceğiz tek paket deposudur.</span><span class="sxs-lookup"><span data-stu-id="00cdd-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="00cdd-109">NuGet.org, topluluk geri bildirimi sağlamak istediğiniz kararlı paketleri ve yayın öncesi paketleri yayımlamak için en iyi yerdir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="00cdd-110">**[Myget](https://myget.org/)** , açık kaynaklı projeler için özel paket akışlarını destekleyen bir depo hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="00cdd-111">Bir MyGet genel özel akışı, CI hizmetiniz tarafından oluşturulan yayın öncesi paketleri yayımlamak için ideal bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="00cdd-112">MyGet ayrıca ticari olarak özel akışlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="00cdd-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="00cdd-113">**[Yerel akış](/nuget/hosting-packages/local-feeds)** , bir klasörü paket deposu gibi davranmanıza ve `*.nupkg` dosyalarını NuGet tarafından erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="00cdd-114">Yerel akış, NuGet.org 'de yayımlamadan önce bir NuGet paketini test etmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="00cdd-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="00cdd-115">NuGet.org, bir paketin karşıya yüklendikten sonra [silinmesine izin vermez](/nuget/policies/deleting-packages) .</span><span class="sxs-lookup"><span data-stu-id="00cdd-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="00cdd-116">Bir paket, Kullanıcı arabiriminde herkese açık olmayan ancak `*.nupkg` hala geri yükleme sırasında indirilebilecek şekilde listelenmemiş şekilde görünmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="00cdd-117">Ayrıca, nuget.org yinelenen paket sürümlerine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="00cdd-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="00cdd-118">Bir NuGet paketini hata ile düzeltmek için yanlış paketi listelemeyi, sürüm numarasını artırmanız ve paketin yeni bir sürümünü yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="00cdd-119">**✔️** , topluluk geri bildirimini NuGet.org 'e göndermek istediğiniz [kararlı paketleri ve yayın öncesi paketleri yayımlayın](/nuget/create-packages/publish-a-package) .</span><span class="sxs-lookup"><span data-stu-id="00cdd-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="00cdd-120">**✔️** yayın öncesi paketleri sürekli tümleştirme derlemesinden bir myget akışına yayımlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="00cdd-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="00cdd-121">**✔️** yerel bir akış veya myget kullanarak geliştirme ortamınızda paketleri test etmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="00cdd-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="00cdd-122">Paketin çalıştığından emin olun ve NuGet.org 'de yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="00cdd-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="00cdd-123">NuGet.org güvenliği</span><span class="sxs-lookup"><span data-stu-id="00cdd-123">NuGet.org security</span></span>

<span data-ttu-id="00cdd-124">Kötü aktörlerin NuGet hesabınıza erişebilmeleri ve kitaplığınızın kötü amaçlı bir sürümünü karşıya yüklemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="00cdd-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="00cdd-125">NuGet.org, bir paket yayımlandığında iki öğeli kimlik doğrulaması ve e-posta bildirimleri sunar.</span><span class="sxs-lookup"><span data-stu-id="00cdd-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="00cdd-126">**Hesap ayarları** sayfasında NuGet.org ' da oturum açtıktan sonra bu özellikleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="00cdd-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="00cdd-127">![alternatif metin](./media/publish-nuget-package/nuget-2fa.png "NuGet hesap güvenliği")</span><span class="sxs-lookup"><span data-stu-id="00cdd-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="00cdd-128">**✔️** NuGet 'de oturum açmak için Microsoft hesabı kullanın.</span><span class="sxs-lookup"><span data-stu-id="00cdd-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="00cdd-129">NuGet 'e erişmek için iki öğeli kimlik doğrulamayı etkinleştirme **✔️** .</span><span class="sxs-lookup"><span data-stu-id="00cdd-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="00cdd-130">bir paket yayımlandığında e-posta bildirimini etkinleştir **✔️** .</span><span class="sxs-lookup"><span data-stu-id="00cdd-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="00cdd-131">[Önceki](sourcelink.md)
>[İleri](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="00cdd-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
