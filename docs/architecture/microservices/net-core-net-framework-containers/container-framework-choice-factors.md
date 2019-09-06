---
title: Karar tablosu. Docker için kullanılacak .NET çerçeveleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Karar tablosu, Docker için kullanılacak .NET çerçeveleri
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296536"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="61077-104">Karar tablosu: Docker için kullanılacak .NET çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="61077-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="61077-105">Aşağıdaki karar tablosu .NET Framework veya .NET Core 'un kullanılıp kullanılmayacağını özetler.</span><span class="sxs-lookup"><span data-stu-id="61077-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="61077-106">Linux kapsayıcılarında, Linux tabanlı Docker konakları (VM 'Ler veya sunucular) gerektiğini ve Windows kapsayıcıları için Windows Server tabanlı Docker konaklarının (VM 'Ler veya sunucular) gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61077-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61077-107">Geliştirme makineleriniz, Linux veya Windows 'un bulunduğu bir Docker ana bilgisayarı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="61077-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="61077-108">Çalıştırmak ve tek bir çözümde birlikte test etmek istediğiniz ilgili mikro hizmetler, tümünün aynı kapsayıcı platformunda çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61077-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="61077-109"><strong>Mimari/uygulama türü</strong></span><span class="sxs-lookup"><span data-stu-id="61077-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="61077-110"><strong>Linux kapsayıcıları</strong></span><span class="sxs-lookup"><span data-stu-id="61077-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="61077-111"><strong>Windows kapsayıcıları</strong></span><span class="sxs-lookup"><span data-stu-id="61077-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="61077-112">Kapsayıcılar üzerinde mikro hizmetler</span><span class="sxs-lookup"><span data-stu-id="61077-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="61077-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-113">.NET Core</span></span></td>
<td><span data-ttu-id="61077-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="61077-115">Tek parçalı uygulama</span><span class="sxs-lookup"><span data-stu-id="61077-115">Monolithic app</span></span></td>
<td><span data-ttu-id="61077-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="61077-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="61077-117">.NET Framework</span></span></p>
<p><span data-ttu-id="61077-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="61077-119">Sınıfının en iyisi performansı ve ölçeklenebilirliği</span><span class="sxs-lookup"><span data-stu-id="61077-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="61077-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-120">.NET Core</span></span></td>
<td><span data-ttu-id="61077-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="61077-122">Windows Server eski uygulaması ("kahverengi-Field") kapsayıcılara geçiş</span><span class="sxs-lookup"><span data-stu-id="61077-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="61077-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="61077-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="61077-124">Yeni kapsayıcı tabanlı geliştirme ("yeşil-alan")</span><span class="sxs-lookup"><span data-stu-id="61077-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="61077-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-125">.NET Core</span></span></td>
<td><span data-ttu-id="61077-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="61077-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="61077-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="61077-129">.NET Core (önerilir)</span><span class="sxs-lookup"><span data-stu-id="61077-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="61077-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="61077-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="61077-131">ASP.NET 4 (MVC 5, Web API 2 ve Web Forms)</span><span class="sxs-lookup"><span data-stu-id="61077-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="61077-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="61077-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="61077-133">SignalR Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="61077-133">SignalR services</span></span></td>
<td><span data-ttu-id="61077-134">.NET Core 2,1 veya üzeri sürümü</span><span class="sxs-lookup"><span data-stu-id="61077-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="61077-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="61077-135">.NET Framework</span></span></p>
<p><span data-ttu-id="61077-136">.NET Core 2,1 veya üzeri sürümü</span><span class="sxs-lookup"><span data-stu-id="61077-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="61077-137">WCF, WF ve diğer eski çerçeveler</span><span class="sxs-lookup"><span data-stu-id="61077-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="61077-138">.NET Core 'da WCF (yalnızca WCF istemci kitaplığı)</span><span class="sxs-lookup"><span data-stu-id="61077-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="61077-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="61077-139">.NET Framework</span></span></p>
<p><span data-ttu-id="61077-140">.NET Core 'da WCF (yalnızca WCF istemci kitaplığı)</span><span class="sxs-lookup"><span data-stu-id="61077-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="61077-141">Azure hizmetleri kullanımı</span><span class="sxs-lookup"><span data-stu-id="61077-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="61077-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-142">.NET Core</span></span></p>
<p><span data-ttu-id="61077-143">(sonuç olarak tüm Azure hizmetleri .NET Core için istemci SDK 'larını sağlar)</span><span class="sxs-lookup"><span data-stu-id="61077-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="61077-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="61077-144">.NET Framework</span></span></p>
<p><span data-ttu-id="61077-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="61077-145">.NET Core</span></span></p>
<p><span data-ttu-id="61077-146">(sonuç olarak tüm Azure hizmetleri .NET Core için istemci SDK 'larını sağlar)</span><span class="sxs-lookup"><span data-stu-id="61077-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="61077-147">[Önceki](net-framework-container-scenarios.md)İleri
>[](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="61077-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>
