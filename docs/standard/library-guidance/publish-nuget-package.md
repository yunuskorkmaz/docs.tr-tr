---
title: Bir NuGet Paketi Yayımlama
description: .NET kitaplıkları için NuGet yayımlamak için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 9c8442b52ed2c54d2fb3368a2e886c5fc2b19148
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640764"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="3c013-103">Bir NuGet Paketi Yayımlama</span><span class="sxs-lookup"><span data-stu-id="3c013-103">Publishing a NuGet package</span></span>

<span data-ttu-id="3c013-104">NuGet paketlerini yayımlandı ve paket depolarından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="3c013-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="3c013-105">NuGet.org bilinen ve kullanılan depo en yaygın olsa da, NuGet paketlerini yayımlamak için pek çok yerde vardır:</span><span class="sxs-lookup"><span data-stu-id="3c013-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="3c013-106">**[NuGet.org](https://www.nuget.org/)**  birincil çevrimiçi için NuGet paketlerini depodur.</span><span class="sxs-lookup"><span data-stu-id="3c013-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="3c013-107">Tüm paketleri NuGet.org üzerinde herkese genel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c013-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="3c013-108">Varsayılan olarak, Visual Studio Paket kaynağı olarak NuGet.org sahiptir ve birçok geliştirici için ile etkileşim kuracağınızı yalnızca paket deposu Nuget.org'nin olduğundan.</span><span class="sxs-lookup"><span data-stu-id="3c013-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="3c013-109">NuGet.org kararlı paketler ve topluluk geri bildirimi almak istediğiniz yayın öncesi paketleri yayımlamak için en iyi yerdir.</span><span class="sxs-lookup"><span data-stu-id="3c013-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="3c013-110">**[MyGet](https://myget.org/)**  , açık kaynak projeleri için özel paket akışları destekleyen bir depo hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="3c013-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="3c013-111">Bir MyGet genel özel akışı CI hizmetiniz tarafından oluşturulan yayın öncesi paketleri yayımlamak için ideal yerdir.</span><span class="sxs-lookup"><span data-stu-id="3c013-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="3c013-112">MyGet ayrıca özel akışları ticari olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c013-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="3c013-113">A **[yerel akış](/nuget/hosting-packages/local-feeds)** yapar ve bir paket deposu gibi bir klasör değerlendirilecek sağlar `*.nupkg` NuGet tarafından erişilebilir klasöründe bulunan dosyaları.</span><span class="sxs-lookup"><span data-stu-id="3c013-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="3c013-114">Yerel bir akış, bir NuGet paketi için NuGet.org yayımlamadan önce test edilmesi için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c013-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="3c013-115">NuGet.org [silinmesi paket izin vermiyor](/nuget/policies/deleting-packages) karşıya yüklendikten sonra.</span><span class="sxs-lookup"><span data-stu-id="3c013-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="3c013-116">Bir paketi kullanıcı Arabiriminde herkese görünür olmaması listelenmemiş olabilir ancak `*.nupkg` geri yükleme yine de indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3c013-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="3c013-117">Ayrıca, nuget.org yinelenen paket sürümlerini izin vermez.</span><span class="sxs-lookup"><span data-stu-id="3c013-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="3c013-118">Bir NuGet paketi yanlış paketi listeden kaldırma için sahip olduğunuz hata gidermek için sürüm numarasını Artır ve paketin yeni bir sürüm yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="3c013-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="3c013-119">**✔️ YAPMAK** [kararlı paketler ve yayın öncesi paketleri yayımlama](/nuget/create-packages/publish-a-package) NuGet.org açın topluluk geri bildirimi istiyor.</span><span class="sxs-lookup"><span data-stu-id="3c013-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="3c013-120">**✔️ DÜŞÜNÜN** sürekli tümleştirme derleme akışı için bir MyGet yayın öncesi paketleri yayımlama.</span><span class="sxs-lookup"><span data-stu-id="3c013-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="3c013-121">**✔️ DÜŞÜNÜN** paketleri yerel akış veya MyGet kullanarak geliştirme ortamınızda test etme.</span><span class="sxs-lookup"><span data-stu-id="3c013-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="3c013-122">Paket çalıştığını denetleyin ardından NuGet.org için yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="3c013-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="3c013-123">NuGet.org güvenlik</span><span class="sxs-lookup"><span data-stu-id="3c013-123">NuGet.org security</span></span>

<span data-ttu-id="3c013-124">Kötü aktörleri NuGet hesabınıza erişmesine olamaz ve kitaplığınızı kötü amaçlı bir sürümünü karşıya önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3c013-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="3c013-125">Bir paketi yayımlandığında NuGet.org iki öğeli kimlik doğrulama ve e-posta bildirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c013-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="3c013-126">Üzerinde NuGet.org oturum açtıktan sonra bu özellikleri etkinleştirmek **hesap ayarları** sayfası.</span><span class="sxs-lookup"><span data-stu-id="3c013-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="3c013-127">![Alternatif metin](./media/publish-nuget-package/nuget-2fa.png "NuGet hesap güvenliği")</span><span class="sxs-lookup"><span data-stu-id="3c013-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="3c013-128">**✔️ YAPMAK** için NuGet oturum açmak için bir Microsoft hesabı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c013-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="3c013-129">**✔️ YAPMAK** NuGet erişmek için iki öğeli kimlik doğrulamasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3c013-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="3c013-130">**✔️ YAPMAK** paketi yayımlandığında e-posta bildirimi etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="3c013-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3c013-131">[Önceki](sourcelink.md)
>[İleri](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="3c013-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
