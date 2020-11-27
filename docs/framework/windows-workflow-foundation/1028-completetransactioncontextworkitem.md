---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 2fc509dac7e13f30f74c24d8b98cba55ed5f8e1d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275121"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="7f512-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="7f512-102">1028 - CompleteTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="7f512-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7f512-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f512-104">ID</span><span class="sxs-lookup"><span data-stu-id="7f512-104">ID</span></span>|<span data-ttu-id="7f512-105">1028</span><span class="sxs-lookup"><span data-stu-id="7f512-105">1028</span></span>|  
|<span data-ttu-id="7f512-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="7f512-106">Keywords</span></span>|<span data-ttu-id="7f512-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7f512-107">WFRuntime</span></span>|  
|<span data-ttu-id="7f512-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="7f512-108">Level</span></span>|<span data-ttu-id="7f512-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="7f512-109">Verbose</span></span>|  
|<span data-ttu-id="7f512-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="7f512-110">Channel</span></span>|<span data-ttu-id="7f512-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="7f512-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7f512-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f512-112">Description</span></span>  

 <span data-ttu-id="7f512-113">Bir TransactionContextWorkItem 'ın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f512-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7f512-114">İleti</span><span class="sxs-lookup"><span data-stu-id="7f512-114">Message</span></span>  

 <span data-ttu-id="7f512-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir TransactionContextWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7f512-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7f512-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7f512-116">Details</span></span>  
  
|<span data-ttu-id="7f512-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7f512-117">Data Item Name</span></span>|<span data-ttu-id="7f512-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7f512-118">Data Item Type</span></span>|<span data-ttu-id="7f512-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f512-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7f512-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="7f512-120">Activity</span></span>|<span data-ttu-id="7f512-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="7f512-121">xs:string</span></span>|<span data-ttu-id="7f512-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="7f512-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7f512-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7f512-123">DisplayName</span></span>|<span data-ttu-id="7f512-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="7f512-124">xs:string</span></span>|<span data-ttu-id="7f512-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="7f512-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7f512-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f512-126">InstanceId</span></span>|<span data-ttu-id="7f512-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="7f512-127">xs:string</span></span>|<span data-ttu-id="7f512-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="7f512-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7f512-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7f512-129">AppDomain</span></span>|<span data-ttu-id="7f512-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="7f512-130">xs:string</span></span>|<span data-ttu-id="7f512-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7f512-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
