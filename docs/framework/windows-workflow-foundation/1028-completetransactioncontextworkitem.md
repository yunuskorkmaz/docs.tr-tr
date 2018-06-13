---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 806a437822cef8802a2bef6a54f924f84c88ef60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511393"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="82b82-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="82b82-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="82b82-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="82b82-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82b82-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="82b82-104">ID</span></span>|<span data-ttu-id="82b82-105">1028</span><span class="sxs-lookup"><span data-stu-id="82b82-105">1028</span></span>|  
|<span data-ttu-id="82b82-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="82b82-106">Keywords</span></span>|<span data-ttu-id="82b82-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="82b82-107">WFRuntime</span></span>|  
|<span data-ttu-id="82b82-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="82b82-108">Level</span></span>|<span data-ttu-id="82b82-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="82b82-109">Verbose</span></span>|  
|<span data-ttu-id="82b82-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="82b82-110">Channel</span></span>|<span data-ttu-id="82b82-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="82b82-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="82b82-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82b82-112">Description</span></span>  
 <span data-ttu-id="82b82-113">Bir TransactionContextWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="82b82-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="82b82-114">İleti</span><span class="sxs-lookup"><span data-stu-id="82b82-114">Message</span></span>  
 <span data-ttu-id="82b82-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="82b82-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="82b82-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="82b82-116">Details</span></span>  
  
|<span data-ttu-id="82b82-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="82b82-117">Data Item Name</span></span>|<span data-ttu-id="82b82-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="82b82-118">Data Item Type</span></span>|<span data-ttu-id="82b82-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82b82-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="82b82-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="82b82-120">Activity</span></span>|<span data-ttu-id="82b82-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="82b82-121">xs:string</span></span>|<span data-ttu-id="82b82-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="82b82-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="82b82-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="82b82-123">DisplayName</span></span>|<span data-ttu-id="82b82-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="82b82-124">xs:string</span></span>|<span data-ttu-id="82b82-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="82b82-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="82b82-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="82b82-126">InstanceId</span></span>|<span data-ttu-id="82b82-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="82b82-127">xs:string</span></span>|<span data-ttu-id="82b82-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="82b82-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="82b82-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="82b82-129">AppDomain</span></span>|<span data-ttu-id="82b82-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="82b82-130">xs:string</span></span>|<span data-ttu-id="82b82-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="82b82-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
