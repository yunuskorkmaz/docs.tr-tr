---
description: 'Daha fazla bilgi edinin: ağ uygulamaları için önbellek yönetimi'
title: Ağ Uygulamaları için Önbellek Yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 6383403b41440f26b29fbb5a22c5b25ee6aab465
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791679"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="9ab03-103">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="9ab03-103">Cache Management for Network Applications</span></span>

<span data-ttu-id="9ab03-104">Bu konu ve ilgili alt konuları,,, <xref:System.Net.WebClient> <xref:System.Net.WebRequest> <xref:System.Net.HttpWebRequest> ve sınıfları kullanılarak elde edilen kaynaklar için önbelleğe almayı anlatmaktadır <xref:System.Net.FtpWebRequest> .</span><span class="sxs-lookup"><span data-stu-id="9ab03-104">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="9ab03-105">Önbellek, bir uygulama tarafından istenen kaynakların geçici olarak depolanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ab03-105">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="9ab03-106">Bir uygulama aynı kaynağı birden çok kez isterse, kaynak önbellekten döndürülebileceğinden, sunucudan yeniden istek yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9ab03-106">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="9ab03-107">Önbelleğe alma, istenen bir kaynağı almak için gereken süreyi azaltarak uygulama performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9ab03-107">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="9ab03-108">Önbelleğe alma, sunucuya gidiş dönüş sayısını azaltarak da ağ trafiğini azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="9ab03-108">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="9ab03-109">Önbelleğe alma performansı artırırken, uygulamaya döndürülen kaynağın eskimiş olması, yani önbelleğe alma kullanımda değilse sunucu tarafından gönderilen kaynakla aynı olmaması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ab03-109">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="9ab03-110">Önbelleğe alma, yetkisiz kullanıcıların veya işlemlerin hassas verileri okumasına izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="9ab03-110">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="9ab03-111">Önbelleğe alınan kimliği doğrulanmış bir yanıt, ek bir yetkilendirme olmadan önbellekten alınabilir.</span><span class="sxs-lookup"><span data-stu-id="9ab03-111">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="9ab03-112">Önbelleğe alma etkinse, <xref:System.Net.WebRequest.CachePolicy%2A> <xref:System.Net.Cache.RequestCacheLevel.BypassCache> <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> Bu istek için önbelleğe almayı devre dışı bırakmak için veya olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9ab03-112">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="9ab03-113">Güvenlik sorunları nedeniyle, orta katman senaryolarında önbelleğe **alma önerilmez.**</span><span class="sxs-lookup"><span data-stu-id="9ab03-113">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ab03-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9ab03-114">In This Section</span></span>  

 [<span data-ttu-id="9ab03-115">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="9ab03-115">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="9ab03-116">Önbellek ilkesinin ne olduğunu ve bir tane tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab03-116">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="9ab03-117">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="9ab03-117">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="9ab03-118">Köprü Metni Aktarım Protokolü (http ve https) kaynakları için kullanılabilen her bir konum tabanlı önbellek ilkesi türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9ab03-118">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="9ab03-119">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="9ab03-119">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="9ab03-120">Zaman tabanlı önbellek ilkesini özelleştirmek için kullanılabilecek kriterleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab03-120">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="9ab03-121">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9ab03-121">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="9ab03-122">Program aracılığıyla önbellek ilkelerinin ve önbelleğe alma kullanan isteklerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab03-122">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9ab03-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9ab03-123">Reference</span></span>  

 <xref:System.Net.Cache>  
 <span data-ttu-id="9ab03-124"><xref:System.Net.WebRequest>, Ve sınıfları kullanılarak elde edilen kaynaklar için önbellek ilkelerini tanımlamak üzere kullanılan türleri ve numaralandırmaları tanımlar <xref:System.Net.HttpWebRequest> <xref:System.Net.FtpWebRequest> .</span><span class="sxs-lookup"><span data-stu-id="9ab03-124">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
