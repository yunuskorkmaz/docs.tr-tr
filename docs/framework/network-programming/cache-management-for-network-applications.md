---
title: "Ağ uygulamaları için önbellek yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 458a1e67e9ca4ff3a36f1b0c69fcc4bdc00be3e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="c813c-102">Ağ uygulamaları için önbellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="c813c-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="c813c-103">Kullanarak elde kaynaklar için önbelleğe alma Bu konu ve alt ilgili konuları açıklanmaktadır <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, ve <xref:System.Net.FtpWebRequest> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c813c-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="c813c-104">Bir önbellek, bir uygulama tarafından istenen kaynakları geçici olarak depolanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c813c-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="c813c-105">Bir uygulama birden çok kez aynı kaynak isterse, kaynak sunucudan yeniden isteme yükünden kurtularak önbellekten döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="c813c-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="c813c-106">Önbelleğe alma, istenen kaynak almak için gereken süreyi azaltarak uygulama performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c813c-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="c813c-107">Önbelleğe alma sunucuya sayısını azaltarak ağ trafiğini da azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c813c-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="c813c-108">Önbelleğe alma performansını artırır, ancak kaynak döndürülen riskini artırır önbelleğe alma kullanılıyor olsalar, sunucu tarafından gönderilen kaynak özdeş değil, yani eski bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="c813c-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="c813c-109">Önbelleğe alma, yetkisiz kullanıcılara veya işlemlere hassas verileri okumak izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="c813c-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="c813c-110">Önbelleğe alınmış bir kimliği doğrulanmış yanıt ek bir yetkilendirme olmadan önbellekten alınabilir.</span><span class="sxs-lookup"><span data-stu-id="c813c-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="c813c-111">Önbelleğe alma etkinse değiştirmek <xref:System.Net.WebRequest.CachePolicy%2A> için <xref:System.Net.Cache.RequestCacheLevel.BypassCache> veya <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> bu istek için önbelleğe almayı devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="c813c-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="c813c-112">Önbelleğe alma güvenlik sorunları nedeniyle olan **değil** orta katman senaryolar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="c813c-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c813c-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c813c-113">In This Section</span></span>  
 [<span data-ttu-id="c813c-114">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="c813c-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="c813c-115">Açıklayan bir önbellek ilkeleri ve nasıl bir tane tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c813c-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="c813c-116">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="c813c-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="c813c-117">Her konum temelli önbellek ilkesi için Köprü Metni Aktarım Protokolü (http ve https) kaynaklar kullanılabilir türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c813c-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="c813c-118">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="c813c-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="c813c-119">Bir zamana dayalı önbellek İlkesi özelleştirmek için kullanılan ölçüt açıklar.</span><span class="sxs-lookup"><span data-stu-id="c813c-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="c813c-120">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c813c-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="c813c-121">Program aracılığıyla önbellek ilkeleri ve önbelleğe alma kullanan istekleri nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c813c-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c813c-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c813c-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="c813c-123">Türleri ve kullanarak elde kaynaklar için önbellek ilkelerini tanımlamak için kullanılan numaralandırmaları tanımlar <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, ve <xref:System.Net.FtpWebRequest> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c813c-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
