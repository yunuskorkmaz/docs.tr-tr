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
ms.openlocfilehash: b3bfe7547fafb17503c972646d344263117d9d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="74da3-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="74da3-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="74da3-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="74da3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74da3-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="74da3-104">ID</span></span>|<span data-ttu-id="74da3-105">4208</span><span class="sxs-lookup"><span data-stu-id="74da3-105">4208</span></span>|  
|<span data-ttu-id="74da3-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="74da3-106">Keywords</span></span>|<span data-ttu-id="74da3-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="74da3-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="74da3-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="74da3-108">Level</span></span>|<span data-ttu-id="74da3-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="74da3-109">Information</span></span>|  
|<span data-ttu-id="74da3-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="74da3-110">Channel</span></span>|<span data-ttu-id="74da3-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="74da3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="74da3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74da3-112">Description</span></span>  
 <span data-ttu-id="74da3-113">SQL sağlayıcısı bir SQL komutu bir SQL hatası nedeniyle yeniden deneniyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="74da3-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="74da3-114">İleti</span><span class="sxs-lookup"><span data-stu-id="74da3-114">Message</span></span>  
 <span data-ttu-id="74da3-115">Bir SQL komutu SQL hata numarası %1 nedeniyle yeniden deneniyor.</span><span class="sxs-lookup"><span data-stu-id="74da3-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="74da3-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="74da3-116">Details</span></span>  
  
|<span data-ttu-id="74da3-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="74da3-117">Data Item Name</span></span>|<span data-ttu-id="74da3-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="74da3-118">Data Item Type</span></span>|<span data-ttu-id="74da3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74da3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="74da3-120">HataNumarası</span><span class="sxs-lookup"><span data-stu-id="74da3-120">ErrorNumber</span></span>|<span data-ttu-id="74da3-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="74da3-121">xs:string</span></span>|<span data-ttu-id="74da3-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="74da3-122">The SQL error number.</span></span>|  
|<span data-ttu-id="74da3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="74da3-123">AppDomain</span></span>|<span data-ttu-id="74da3-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="74da3-124">xs:string</span></span>|<span data-ttu-id="74da3-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="74da3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
