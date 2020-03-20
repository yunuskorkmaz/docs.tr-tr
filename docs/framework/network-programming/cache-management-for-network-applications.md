---
title: Ağ Uygulamaları için Önbellek Yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048881"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="a269b-102">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="a269b-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="a269b-103">Bu <xref:System.Net.WebClient>konu ve ilgili alt konuları, , , <xref:System.Net.WebRequest> <xref:System.Net.HttpWebRequest>ve <xref:System.Net.FtpWebRequest> sınıflar kullanılarak elde edilen kaynaklar için önbelleğe alma açıklar.</span><span class="sxs-lookup"><span data-stu-id="a269b-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="a269b-104">Önbellek, bir uygulama tarafından istenen kaynakların geçici olarak depolanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a269b-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="a269b-105">Bir uygulama aynı kaynağı birden çok kez isterse, kaynak sunucudan yeniden talep etme yükünden kaçınarak önbellekten döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="a269b-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="a269b-106">Önbelleğe alma, istenen bir kaynağı elde etmek için gereken süreyi azaltarak uygulama performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="a269b-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="a269b-107">Önbelleğe alma, sunucuya yapılan seyahat sayısını azaltarak ağ trafiğini de azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="a269b-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="a269b-108">Önbelleğe alma performansı artırırken, uygulamaya döndürülen kaynağın eskimiş olması riskini artırır, bu da önbelleğe alma kullanılmamışsa sunucu tarafından gönderilen kaynakla aynı olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a269b-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="a269b-109">Önbelleğe alma, yetkisiz kullanıcıların veya işlemlerin hassas verileri okumasına izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="a269b-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="a269b-110">Önbelleğe alınmış kimlik doğrulaması yanıtı ek bir yetkilendirme olmadan önbellekten alınabilir.</span><span class="sxs-lookup"><span data-stu-id="a269b-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="a269b-111">Önbelleğe alma etkinse, <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> bu istek için önbelleğe alma veya devre dışı etme özelliğini değiştirin. <xref:System.Net.WebRequest.CachePolicy%2A> <xref:System.Net.Cache.RequestCacheLevel.BypassCache></span><span class="sxs-lookup"><span data-stu-id="a269b-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="a269b-112">Güvenlik kaygıları nedeniyle, önbelleğe alma orta katman senaryoları için **önerilmez.**</span><span class="sxs-lookup"><span data-stu-id="a269b-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a269b-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a269b-113">In This Section</span></span>  
 [<span data-ttu-id="a269b-114">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="a269b-114">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="a269b-115">Önbellek ilkesinin ne olduğunu ve nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a269b-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="a269b-116">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="a269b-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="a269b-117">Hypertext Aktarım Protokolü (http ve https) kaynakları için kullanılabilen her konum tabanlı önbellek ilkesi türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a269b-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="a269b-118">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="a269b-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="a269b-119">Zaman tabanlı önbellek ilkesini özelleştirmek için kullanılabilecek ölçütleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a269b-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="a269b-120">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a269b-120">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="a269b-121">Önbellek kullanan önbellek ilkeleri ve isteklerini programlı bir şekilde nasıl oluşturacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a269b-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a269b-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a269b-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="a269b-123"><xref:System.Net.WebRequest>, , <xref:System.Net.HttpWebRequest>ve sınıflar kullanılarak elde edilen kaynaklar için önbellek ilkelerini tanımlamak için kullanılan türleri ve <xref:System.Net.FtpWebRequest> sayısallaştırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a269b-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
