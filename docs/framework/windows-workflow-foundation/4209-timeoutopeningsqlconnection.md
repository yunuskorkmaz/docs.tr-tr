---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513171"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="a6ddc-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="a6ddc-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="a6ddc-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a6ddc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6ddc-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a6ddc-104">ID</span></span>|<span data-ttu-id="a6ddc-105">4209</span><span class="sxs-lookup"><span data-stu-id="a6ddc-105">4209</span></span>|  
|<span data-ttu-id="a6ddc-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a6ddc-106">Keywords</span></span>|<span data-ttu-id="a6ddc-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="a6ddc-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="a6ddc-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a6ddc-108">Level</span></span>|<span data-ttu-id="a6ddc-109">Hata</span><span class="sxs-lookup"><span data-stu-id="a6ddc-109">Error</span></span>|  
|<span data-ttu-id="a6ddc-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a6ddc-110">Channel</span></span>|<span data-ttu-id="a6ddc-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a6ddc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a6ddc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6ddc-112">Description</span></span>  
 <span data-ttu-id="a6ddc-113">SQL bağlantısı açılmaya çalışırken zaman aşımı oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6ddc-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a6ddc-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a6ddc-114">Message</span></span>  
 <span data-ttu-id="a6ddc-115">SQL bağlantısı açılmaya çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="a6ddc-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="a6ddc-116">İşlemi %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="a6ddc-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="a6ddc-117">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6ddc-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a6ddc-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a6ddc-118">Details</span></span>  
  
|<span data-ttu-id="a6ddc-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a6ddc-119">Data Item Name</span></span>|<span data-ttu-id="a6ddc-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a6ddc-120">Data Item Type</span></span>|<span data-ttu-id="a6ddc-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6ddc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a6ddc-122">Zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="a6ddc-122">Timeout</span></span>|<span data-ttu-id="a6ddc-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="a6ddc-123">xs:string</span></span>|<span data-ttu-id="a6ddc-124">SQL Bağlantısı açmak için zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="a6ddc-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="a6ddc-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a6ddc-125">AppDomain</span></span>|<span data-ttu-id="a6ddc-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="a6ddc-126">xs:string</span></span>|<span data-ttu-id="a6ddc-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a6ddc-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
