---
title: Karar tablosu. Docker için kullanılacak .NET çerçeveleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Karar tablosu, Docker için kullanılacak .NET çerçeveleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 8044e3064ac372750c174d8b47c3f7a63d6bbd0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864097"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="efbaf-104">Karar tablosu: Docker için kullanılacak .NET çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="efbaf-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="efbaf-105">Aşağıdaki tabloda karar .NET Framework veya .NET Core kullanıp kullanmayacağınızı özetler.</span><span class="sxs-lookup"><span data-stu-id="efbaf-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="efbaf-106">Linux kapsayıcıları için Linux tabanlı Docker konakları (VM'ler veya sunucular) gerekir ve Docker ana bilgisayarları (VM'ler veya sunucular) tabanlı Windows kapsayıcıları için Windows Server ihtiyacınız olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="efbaf-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efbaf-107">Geliştirme makineleriniz bir Docker konağı, Linux veya Windows çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="efbaf-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="efbaf-108">İlgili mikro hizmetler ve birlikte bir çözümde test çalıştırmak istediğiniz tüm aynı kapsayıcı platformu üzerinde çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="efbaf-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="efbaf-109"><strong>Mimari / uygulama yazın</strong></span><span class="sxs-lookup"><span data-stu-id="efbaf-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="efbaf-110"><strong>Linux kapsayıcıları</strong></span><span class="sxs-lookup"><span data-stu-id="efbaf-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="efbaf-111"><strong>Windows kapsayıcıları</strong></span><span class="sxs-lookup"><span data-stu-id="efbaf-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="efbaf-112">Kapsayıcıları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="efbaf-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="efbaf-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-113">.NET Core</span></span></td>
<td><span data-ttu-id="efbaf-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="efbaf-115">Tek parçalı uygulama</span><span class="sxs-lookup"><span data-stu-id="efbaf-115">Monolithic app</span></span></td>
<td><span data-ttu-id="efbaf-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="efbaf-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efbaf-117">.NET Framework</span></span></p>
<p><span data-ttu-id="efbaf-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="efbaf-119">Sınıfının en iyi performans ve ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="efbaf-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="efbaf-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-120">.NET Core</span></span></td>
<td><span data-ttu-id="efbaf-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="efbaf-122">Windows Server kapsayıcıları için eski uygulama ("alanı brown") geçiş</span><span class="sxs-lookup"><span data-stu-id="efbaf-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="efbaf-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efbaf-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="efbaf-124">Yeni kapsayıcı tabanlı geliştirme ("alanı yeşil")</span><span class="sxs-lookup"><span data-stu-id="efbaf-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="efbaf-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-125">.NET Core</span></span></td>
<td><span data-ttu-id="efbaf-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="efbaf-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="efbaf-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="efbaf-129">.NET core (önerilir)</span><span class="sxs-lookup"><span data-stu-id="efbaf-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="efbaf-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efbaf-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="efbaf-131">ASP.NET 4 (MVC 5, Web API 2 ve Web Forms)</span><span class="sxs-lookup"><span data-stu-id="efbaf-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="efbaf-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efbaf-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="efbaf-133">SignalR Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="efbaf-133">SignalR services</span></span></td>
<td><span data-ttu-id="efbaf-134">.NET core 2.1 veya üzeri bir sürüm</span><span class="sxs-lookup"><span data-stu-id="efbaf-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="efbaf-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efbaf-135">.NET Framework</span></span></p>
<p><span data-ttu-id="efbaf-136">.NET core 2.1 veya üzeri bir sürüm</span><span class="sxs-lookup"><span data-stu-id="efbaf-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="efbaf-137">WCF, WF ve diğer eski çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="efbaf-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="efbaf-138">WCF .NET core'da (yalnızca WCF istemci kitaplığı)</span><span class="sxs-lookup"><span data-stu-id="efbaf-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="efbaf-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efbaf-139">.NET Framework</span></span></p>
<p><span data-ttu-id="efbaf-140">WCF .NET core'da (yalnızca WCF istemci kitaplığı)</span><span class="sxs-lookup"><span data-stu-id="efbaf-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="efbaf-141">Azure hizmetlerinin tüketiminin</span><span class="sxs-lookup"><span data-stu-id="efbaf-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="efbaf-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-142">.NET Core</span></span></p>
<p><span data-ttu-id="efbaf-143">(sonunda tüm Azure Hizmetleri İstemci SDK'ları için .NET Core sağlar)</span><span class="sxs-lookup"><span data-stu-id="efbaf-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="efbaf-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efbaf-144">.NET Framework</span></span></p>
<p><span data-ttu-id="efbaf-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="efbaf-145">.NET Core</span></span></p>
<p><span data-ttu-id="efbaf-146">(sonunda tüm Azure Hizmetleri İstemci SDK'ları için .NET Core sağlar)</span><span class="sxs-lookup"><span data-stu-id="efbaf-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="efbaf-147">[Önceki](net-framework-container-scenarios.md)
>[İleri](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="efbaf-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>