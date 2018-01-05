---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51374a25ee11b3344e950670cc7882db42d39779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="5da8f-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="5da8f-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="5da8f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5da8f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5da8f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="5da8f-104">ID</span></span>|<span data-ttu-id="5da8f-105">4208</span><span class="sxs-lookup"><span data-stu-id="5da8f-105">4208</span></span>|  
|<span data-ttu-id="5da8f-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="5da8f-106">Keywords</span></span>|<span data-ttu-id="5da8f-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5da8f-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5da8f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5da8f-108">Level</span></span>|<span data-ttu-id="5da8f-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="5da8f-109">Information</span></span>|  
|<span data-ttu-id="5da8f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5da8f-110">Channel</span></span>|<span data-ttu-id="5da8f-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5da8f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5da8f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5da8f-112">Description</span></span>  
 <span data-ttu-id="5da8f-113">SQL sağlayıcısı bir SQL komutu bir SQL hatası nedeniyle yeniden deneniyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="5da8f-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5da8f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="5da8f-114">Message</span></span>  
 <span data-ttu-id="5da8f-115">Bir SQL komutu SQL hata numarası %1 nedeniyle yeniden deneniyor.</span><span class="sxs-lookup"><span data-stu-id="5da8f-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5da8f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5da8f-116">Details</span></span>  
  
|<span data-ttu-id="5da8f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5da8f-117">Data Item Name</span></span>|<span data-ttu-id="5da8f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5da8f-118">Data Item Type</span></span>|<span data-ttu-id="5da8f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5da8f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5da8f-120">HataNumarası</span><span class="sxs-lookup"><span data-stu-id="5da8f-120">ErrorNumber</span></span>|<span data-ttu-id="5da8f-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="5da8f-121">xs:string</span></span>|<span data-ttu-id="5da8f-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="5da8f-122">The SQL error number.</span></span>|  
|<span data-ttu-id="5da8f-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5da8f-123">AppDomain</span></span>|<span data-ttu-id="5da8f-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="5da8f-124">xs:string</span></span>|<span data-ttu-id="5da8f-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5da8f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
