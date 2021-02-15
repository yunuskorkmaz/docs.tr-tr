---
title: ASP.NET Identity ve ASP.NET Core kimliğini karşılaştırın
description: Bu bölümde ASP.NET Identity ve ASP.NET Core kimliği arasındaki farklar incelanıyor. Bu, .NET Framework ' den .NET Core 'a geçiş planlarken özellikle önemlidir.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: bf915c7343b0c8060ef8192387a3cec33a1f0eea
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488887"
---
# <a name="compare-aspnet-identity-and-aspnet-core-identity"></a><span data-ttu-id="cd38a-103">ASP.NET Identity ve ASP.NET Core kimliğini karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="cd38a-103">Compare ASP.NET Identity and ASP.NET Core Identity</span></span>

<span data-ttu-id="cd38a-104">ASP.NET MVC 'de, kimlik özellikleri genellikle *App_Start* klasöründe *IdentityConfig.cs* ' de yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="cd38a-104">In ASP.NET MVC, identity features are typically configured in *IdentityConfig.cs* in the *App_Start* folder.</span></span> <span data-ttu-id="cd38a-105">Bunun mevcut uygulamada nasıl yapılandırıldığını gözden geçirin ve *Startup.cs* Içinde [ASP.NET Core kimliği için gereken yapılandırmayla](https://docs.microsoft.com/aspnet/core/security/authentication/identity-configuration) karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="cd38a-105">Review how this is configured in the existing app, and compare it to the [configuration required for ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity-configuration) in *Startup.cs*.</span></span>

<span data-ttu-id="cd38a-106">ASP.NET Identity, Kullanıcı arabirimi oturum açma işlevselliğini destekleyen ve kullanıcıları, parolaları, profil verilerini, rolleri, talepleri, belirteçleri, e-posta onaylarını ve daha fazlasını yöneten bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="cd38a-106">ASP.NET Identity is an API that supports user interface login functionality and manages users, passwords, profile data, roles, claims, tokens, email confirmations, and more.</span></span> <span data-ttu-id="cd38a-107">Facebook, Google, Microsoft ve Twitter gibi dış oturum açma sağlayıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="cd38a-107">It supports external login providers like Facebook, Google, Microsoft, and Twitter.</span></span>

<span data-ttu-id="cd38a-108">ASP.NET MVC uygulamanız ASP.NET üyeliğini kullanıyorsa, [ASP.NET üyelik kimlik doğrulamasından ASP.NET Core 2,0 kimliğine geçiş](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)kılavuzunu bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cd38a-108">If your ASP.NET MVC app is using ASP.NET Membership, you'll find a guide to [migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="cd38a-109">Bu temel olarak, geçirilen Kullanıcı kayıtlarıyla ASP.NET Core kimliğini kullanabilmeniz için bir veri geçiş alýþtýrmadır.</span><span class="sxs-lookup"><span data-stu-id="cd38a-109">This is mainly a data migration exercise, at the completion of which you should be able to use ASP.NET Core Identity with your migrated user records.</span></span>

<span data-ttu-id="cd38a-110">ASP.NET Identity kullanıcılarınızı ASP.NET Core kimliğe geçirirseniz, parola karmalarını güncelleştirmeniz veya yeni ASP.NET Core kimlik yaklaşımına veya eski ASP.NET Identity yaklaşımıyla hangi parolaların karma olduğunu izlemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cd38a-110">If you migrate your ASP.NET Identity users to ASP.NET Core Identity, you may need to update their password hashes, or track which passwords are hashed with the new ASP.NET Core Identity approach or the older ASP.NET Identity approach.</span></span> <span data-ttu-id="cd38a-111">[Stack Overflow açıklanan bu yaklaşım](https://stackoverflow.com/a/57074910/13729) , Kullanıcı parolası karmalarının tek seferde değil, zaman içinde geçirilmesi için bazı seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd38a-111">[This approach described on Stack Overflow](https://stackoverflow.com/a/57074910/13729) provides some options for migrating user password hashes over time, rather than all at once.</span></span>

<span data-ttu-id="cd38a-112">ASP.NET Identity karşılaştırılan ASP.NET Core kimliği için verilen en büyük farklardan biri, projenize dahil etmeniz gereken küçük kod.</span><span class="sxs-lookup"><span data-stu-id="cd38a-112">One of the biggest differences when it comes to ASP.NET Core Identity compared to ASP.NET Identity is how little code you need to include in your project.</span></span> <span data-ttu-id="cd38a-113">ASP.NET Core kimlik artık Razor sınıf kitaplığı olarak gelir, yani Kullanıcı arabirimi ve Logic bir NuGet paketinden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd38a-113">ASP.NET Core Identity now ships as a Razor Class Library, meaning its UI and logic are all available from a NuGet package.</span></span> <span data-ttu-id="cd38a-114">[ASP.NET Core kimlik dosyalarını](https://docs.microsoft.com/aspnet/core/security/authentication/scaffold-identity) düzenleyerek mevcut kullanıcı arabirimini ve mantığı geçersiz kılabilirsiniz, ancak bu durumda, yalnızca değiştirmek istediğiniz sayfaları, var olan her birini değil yalnızca yapı birimi için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd38a-114">You can override the existing UI and logic by [scaffolding the ASP.NET Core Identity files](https://docs.microsoft.com/aspnet/core/security/authentication/scaffold-identity) but even in this case you need only scaffold the pages you want to modify, not every one that exists.</span></span>

## <a name="migrate-from-owin--katana"></a><span data-ttu-id="cd38a-115">OWıN/Katana 'dan geçiş</span><span class="sxs-lookup"><span data-stu-id="cd38a-115">Migrate from OWIN / Katana</span></span>

<span data-ttu-id="cd38a-116">Aşağıdaki kaynaklar OWıN/Katana 'dan geçiş için bazı rehberlik sunar:</span><span class="sxs-lookup"><span data-stu-id="cd38a-116">The following resources offer some guidance for migrating from OWIN / Katana:</span></span>

- [<span data-ttu-id="cd38a-117">Geçiş</span><span class="sxs-lookup"><span data-stu-id="cd38a-117">Migration</span></span>](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/#globalasax-file-replacement)
- [<span data-ttu-id="cd38a-118">Bir katana, ASPNET 5</span><span class="sxs-lookup"><span data-stu-id="cd38a-118">Katana to ASPNET 5</span></span>](https://devblogs.microsoft.com/aspnet/katana-asp-net-5-and-bridging-the-gap/)

## <a name="references"></a><span data-ttu-id="cd38a-119">Başvurular</span><span class="sxs-lookup"><span data-stu-id="cd38a-119">References</span></span>

- [<span data-ttu-id="cd38a-120">Kimlik doğrulaması ve kimliği ASP.NET Core geçir</span><span class="sxs-lookup"><span data-stu-id="cd38a-120">Migrate Authentication and Identity to ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/migration/identity)
- [<span data-ttu-id="cd38a-121">ASP.NET Core kimliğe giriş</span><span class="sxs-lookup"><span data-stu-id="cd38a-121">Introduction to Identity on ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)
- [<span data-ttu-id="cd38a-122">ASP.NET Core kimliğini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cd38a-122">Configure ASP.NET Core Identity</span></span>](https://docs.microsoft.com/aspnet/core/security/authentication/identity-configuration)
- [<span data-ttu-id="cd38a-123">ASP.NET Core projelerinde yapı iskelesi kimliği</span><span class="sxs-lookup"><span data-stu-id="cd38a-123">Scaffold Identity in ASP.NET Core projects</span></span>](https://docs.microsoft.com/aspnet/core/security/authentication/scaffold-identity)

>[!div class="step-by-step"]
><span data-ttu-id="cd38a-124">[Önceki](authentication-differences.md) 
> [Sonraki](controller-differences.md)</span><span class="sxs-lookup"><span data-stu-id="cd38a-124">[Previous](authentication-differences.md)
[Next](controller-differences.md)</span></span>
