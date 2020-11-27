---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: cb5671ce7a30a7096104ba0ca6c4f36bed6b93f9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275238"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="1bddc-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="1bddc-102">1027 - StartTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="1bddc-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1bddc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1bddc-104">ID</span><span class="sxs-lookup"><span data-stu-id="1bddc-104">ID</span></span>|<span data-ttu-id="1bddc-105">1027</span><span class="sxs-lookup"><span data-stu-id="1bddc-105">1027</span></span>|  
|<span data-ttu-id="1bddc-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="1bddc-106">Keywords</span></span>|<span data-ttu-id="1bddc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1bddc-107">WFRuntime</span></span>|  
|<span data-ttu-id="1bddc-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1bddc-108">Level</span></span>|<span data-ttu-id="1bddc-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="1bddc-109">Verbose</span></span>|  
|<span data-ttu-id="1bddc-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1bddc-110">Channel</span></span>|<span data-ttu-id="1bddc-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="1bddc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1bddc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bddc-112">Description</span></span>  

 <span data-ttu-id="1bddc-113">Bir TransactionContextWorkItem 'ın yürütülmeye başlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bddc-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1bddc-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1bddc-114">Message</span></span>  

 <span data-ttu-id="1bddc-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir TransactionContextWorkItem 'ın yürütülmesi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="1bddc-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1bddc-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1bddc-116">Details</span></span>  
  
|<span data-ttu-id="1bddc-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1bddc-117">Data Item Name</span></span>|<span data-ttu-id="1bddc-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1bddc-118">Data Item Type</span></span>|<span data-ttu-id="1bddc-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bddc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1bddc-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="1bddc-120">Activity</span></span>|<span data-ttu-id="1bddc-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bddc-121">xs:string</span></span>|<span data-ttu-id="1bddc-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="1bddc-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1bddc-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1bddc-123">DisplayName</span></span>|<span data-ttu-id="1bddc-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bddc-124">xs:string</span></span>|<span data-ttu-id="1bddc-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="1bddc-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1bddc-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1bddc-126">InstanceId</span></span>|<span data-ttu-id="1bddc-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bddc-127">xs:string</span></span>|<span data-ttu-id="1bddc-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="1bddc-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1bddc-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1bddc-129">AppDomain</span></span>|<span data-ttu-id="1bddc-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="1bddc-130">xs:string</span></span>|<span data-ttu-id="1bddc-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1bddc-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
