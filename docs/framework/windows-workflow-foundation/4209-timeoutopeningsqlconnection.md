---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774276"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="9ef9d-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="9ef9d-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="9ef9d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9ef9d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ef9d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9ef9d-104">ID</span></span>|<span data-ttu-id="9ef9d-105">4209</span><span class="sxs-lookup"><span data-stu-id="9ef9d-105">4209</span></span>|  
|<span data-ttu-id="9ef9d-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9ef9d-106">Keywords</span></span>|<span data-ttu-id="9ef9d-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="9ef9d-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="9ef9d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9ef9d-108">Level</span></span>|<span data-ttu-id="9ef9d-109">Hata</span><span class="sxs-lookup"><span data-stu-id="9ef9d-109">Error</span></span>|  
|<span data-ttu-id="9ef9d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9ef9d-110">Channel</span></span>|<span data-ttu-id="9ef9d-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9ef9d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ef9d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ef9d-112">Description</span></span>  
 <span data-ttu-id="9ef9d-113">Bir SQL bağlantı açılmaya çalışılırken zaman aşımıyla karşılaşıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ef9d-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ef9d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9ef9d-114">Message</span></span>  
 <span data-ttu-id="9ef9d-115">Bir SQL bağlantı açılmaya çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="9ef9d-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="9ef9d-116">İşlem, %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="9ef9d-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="9ef9d-117">Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ef9d-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ef9d-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9ef9d-118">Details</span></span>  
  
|<span data-ttu-id="9ef9d-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9ef9d-119">Data Item Name</span></span>|<span data-ttu-id="9ef9d-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9ef9d-120">Data Item Type</span></span>|<span data-ttu-id="9ef9d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ef9d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ef9d-122">zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="9ef9d-122">Timeout</span></span>|<span data-ttu-id="9ef9d-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef9d-123">xs:string</span></span>|<span data-ttu-id="9ef9d-124">SQL Bağlantısı açmak için zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="9ef9d-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="9ef9d-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ef9d-125">AppDomain</span></span>|<span data-ttu-id="9ef9d-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef9d-126">xs:string</span></span>|<span data-ttu-id="9ef9d-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9ef9d-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
