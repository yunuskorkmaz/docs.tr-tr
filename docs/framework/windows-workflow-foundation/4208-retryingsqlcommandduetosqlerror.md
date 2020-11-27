---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 088754cb15c2e55faa1d43a1da1c79ddcddd69f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280422"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="90559-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="90559-102">4208 - RetryingSqlCommandDueToSqlError</span></span>

## <a name="properties"></a><span data-ttu-id="90559-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="90559-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90559-104">ID</span><span class="sxs-lookup"><span data-stu-id="90559-104">ID</span></span>|<span data-ttu-id="90559-105">4208</span><span class="sxs-lookup"><span data-stu-id="90559-105">4208</span></span>|  
|<span data-ttu-id="90559-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="90559-106">Keywords</span></span>|<span data-ttu-id="90559-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="90559-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="90559-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="90559-108">Level</span></span>|<span data-ttu-id="90559-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="90559-109">Information</span></span>|  
|<span data-ttu-id="90559-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="90559-110">Channel</span></span>|<span data-ttu-id="90559-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="90559-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="90559-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90559-112">Description</span></span>  

 <span data-ttu-id="90559-113">SQL sağlayıcısı 'nın bir SQL hatası nedeniyle bir SQL komutu yeniden denediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="90559-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="90559-114">İleti</span><span class="sxs-lookup"><span data-stu-id="90559-114">Message</span></span>  

 <span data-ttu-id="90559-115">%1 numaralı SQL hatası nedeniyle bir SQL komutu yeniden deneniyor.</span><span class="sxs-lookup"><span data-stu-id="90559-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="90559-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="90559-116">Details</span></span>  
  
|<span data-ttu-id="90559-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="90559-117">Data Item Name</span></span>|<span data-ttu-id="90559-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="90559-118">Data Item Type</span></span>|<span data-ttu-id="90559-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90559-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="90559-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="90559-120">ErrorNumber</span></span>|<span data-ttu-id="90559-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="90559-121">xs:string</span></span>|<span data-ttu-id="90559-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="90559-122">The SQL error number.</span></span>|  
|<span data-ttu-id="90559-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="90559-123">AppDomain</span></span>|<span data-ttu-id="90559-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="90559-124">xs:string</span></span>|<span data-ttu-id="90559-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="90559-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
