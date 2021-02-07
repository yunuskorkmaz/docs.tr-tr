---
description: 'Hakkında daha fazla bilgi edinin: 4208-RetryingSqlCommandDueToSqlError'
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 11ea2260f6a2ceffc1ffdbfce2cb3e3ce784076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755310"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="5bbbb-103">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="5bbbb-103">4208 - RetryingSqlCommandDueToSqlError</span></span>

## <a name="properties"></a><span data-ttu-id="5bbbb-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5bbbb-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bbbb-105">ID</span><span class="sxs-lookup"><span data-stu-id="5bbbb-105">ID</span></span>|<span data-ttu-id="5bbbb-106">4208</span><span class="sxs-lookup"><span data-stu-id="5bbbb-106">4208</span></span>|  
|<span data-ttu-id="5bbbb-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5bbbb-107">Keywords</span></span>|<span data-ttu-id="5bbbb-108">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="5bbbb-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="5bbbb-109">Level</span><span class="sxs-lookup"><span data-stu-id="5bbbb-109">Level</span></span>|<span data-ttu-id="5bbbb-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="5bbbb-110">Information</span></span>|  
|<span data-ttu-id="5bbbb-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="5bbbb-111">Channel</span></span>|<span data-ttu-id="5bbbb-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="5bbbb-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5bbbb-113">Description</span><span class="sxs-lookup"><span data-stu-id="5bbbb-113">Description</span></span>  

 <span data-ttu-id="5bbbb-114">SQL sağlayıcısı 'nın bir SQL hatası nedeniyle bir SQL komutu yeniden denediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-114">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5bbbb-115">İleti</span><span class="sxs-lookup"><span data-stu-id="5bbbb-115">Message</span></span>  

 <span data-ttu-id="5bbbb-116">%1 numaralı SQL hatası nedeniyle bir SQL komutu yeniden deneniyor.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-116">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5bbbb-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5bbbb-117">Details</span></span>  
  
|<span data-ttu-id="5bbbb-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5bbbb-118">Data Item Name</span></span>|<span data-ttu-id="5bbbb-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5bbbb-119">Data Item Type</span></span>|<span data-ttu-id="5bbbb-120">Description</span><span class="sxs-lookup"><span data-stu-id="5bbbb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5bbbb-121">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="5bbbb-121">ErrorNumber</span></span>|<span data-ttu-id="5bbbb-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="5bbbb-122">xs:string</span></span>|<span data-ttu-id="5bbbb-123">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-123">The SQL error number.</span></span>|  
|<span data-ttu-id="5bbbb-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5bbbb-124">AppDomain</span></span>|<span data-ttu-id="5bbbb-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="5bbbb-125">xs:string</span></span>|<span data-ttu-id="5bbbb-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
