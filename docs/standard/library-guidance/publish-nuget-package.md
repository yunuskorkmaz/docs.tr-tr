---
title: NuGet paketini yayımlama
description: .NET kitaplıklarını NuGet'e yayınlamak için en iyi uygulama önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744558"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="a41f9-103">NuGet paketini yayımlama</span><span class="sxs-lookup"><span data-stu-id="a41f9-103">Publishing a NuGet package</span></span>

<span data-ttu-id="a41f9-104">NuGet paketleri paket depolarından yayınlanır ve tüketilir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="a41f9-105">NuGet.org en yaygın olarak bilinen ve kullanılan depo olmakla birlikte, NuGet paketlerini yayınlamak için birçok yer vardır:</span><span class="sxs-lookup"><span data-stu-id="a41f9-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="a41f9-106">**[NuGet.org](https://www.nuget.org/)** NuGet paketleri için birincil çevrimiçi depodur.</span><span class="sxs-lookup"><span data-stu-id="a41f9-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="a41f9-107">NuGet.org tüm paketler herkese açıktır.</span><span class="sxs-lookup"><span data-stu-id="a41f9-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="a41f9-108">Varsayılan olarak, Visual Studio bir paket kaynağı olarak NuGet.org ve birçok geliştirici için NuGet.org etkileşim edeceğiz tek paket deposudur.</span><span class="sxs-lookup"><span data-stu-id="a41f9-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="a41f9-109">NuGet.org, topluluk geri bildirimi istediğiniz kararlı paketleri ve yayın öncesi paketleri yayınlamak için en iyi yerdir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="a41f9-110">**[MyGet,](https://myget.org/)** açık kaynak projeleri için özel paket akışlarını destekleyen bir depo hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="a41f9-111">MyGet genel özel akışı, CI hizmetiniz tarafından oluşturulan yayın öncesi paketleri yayınlamak için ideal bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="a41f9-112">MyGet ayrıca ticari olarak özel yayınlar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="a41f9-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="a41f9-113">**[Yerel özet akışı,](/nuget/hosting-packages/local-feeds)** bir klasörü paket deposu gibi ele `*.nupkg` almanıza olanak tanır ve klasördeki dosyaları NuGet tarafından erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="a41f9-114">Yerel özet akışı, nuget paketini NuGet.org yayınlamadan önce sınamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a41f9-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="a41f9-115">NuGet.org bir paketin yüklendikten sonra [silinmesine izin vermez.](/nuget/policies/deleting-packages)</span><span class="sxs-lookup"><span data-stu-id="a41f9-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="a41f9-116">Bir paket, UI'de herkese açık olarak görülmeyecek, `*.nupkg` ancak yine de geri yüklenebilecek şekilde liste dışı tutulabilir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="a41f9-117">Ayrıca, nuget.org yinelenen paket sürümlerine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="a41f9-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="a41f9-118">NuGet paketini bir hatayla düzeltmek için yanlış paketin listesini iptal etmeniz, sürüm numarasını artımve paketin yeni bir sürümünü yayınlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="a41f9-119">do ✔️, topluluk geri bildiriminin NuGet.org için olmasını istediğiniz [kararlı paketleri ve yayın öncesi paketleri yayımlar.](/nuget/create-packages/publish-a-package)</span><span class="sxs-lookup"><span data-stu-id="a41f9-119">✔️ DO [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="a41f9-120">✔️, sürekli bir tümleştirme yapısından MyGet akışına yayın öncesi paketleri yayınlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="a41f9-120">✔️ CONSIDER publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="a41f9-121">✔️ yerel bir özet akışı veya MyGet kullanarak geliştirme ortamınızdaki paketleri test etmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="a41f9-121">✔️ CONSIDER testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="a41f9-122">Paket çalışmalarını denetleyin ve ardından NuGet.org yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="a41f9-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="a41f9-123">NuGet.org güvenliği</span><span class="sxs-lookup"><span data-stu-id="a41f9-123">NuGet.org security</span></span>

<span data-ttu-id="a41f9-124">Kötü aktörlerin NuGet hesabınıza erişememesi ve kitaplığınızın kötü amaçlı bir sürümünü yükleyemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a41f9-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="a41f9-125">NuGet.org, paket yayımlandığında iki faktörlü kimlik doğrulama ve e-posta bildirimleri sunar.</span><span class="sxs-lookup"><span data-stu-id="a41f9-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="a41f9-126">**Hesap ayarları** sayfasında NuGet.org giriş yaptıktan sonra bu özellikleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a41f9-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="a41f9-127">![alternatif metin](./media/publish-nuget-package/nuget-2fa.png "NuGet Hesap Güvenliği")</span><span class="sxs-lookup"><span data-stu-id="a41f9-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="a41f9-128">✔️ Do NuGet oturum için bir Microsoft hesabı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a41f9-128">✔️ DO use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="a41f9-129">✔️ DO NuGet erişmek için iki faktörlü kimlik doğrulama etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a41f9-129">✔️ DO enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="a41f9-130">✔️ bir paket yayımlandığında e-posta bildirimini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a41f9-130">✔️ DO enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a41f9-131">[Önceki](sourcelink.md)
>[Sonraki](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="a41f9-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
