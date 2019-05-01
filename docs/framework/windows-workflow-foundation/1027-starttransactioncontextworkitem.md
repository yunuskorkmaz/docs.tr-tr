---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: 231a7607f2ce9a38e8dd6c1486a68bc9eb459e5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008830"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="e9781-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="e9781-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e9781-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e9781-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9781-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e9781-104">ID</span></span>|<span data-ttu-id="e9781-105">1027</span><span class="sxs-lookup"><span data-stu-id="e9781-105">1027</span></span>|  
|<span data-ttu-id="e9781-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e9781-106">Keywords</span></span>|<span data-ttu-id="e9781-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e9781-107">WFRuntime</span></span>|  
|<span data-ttu-id="e9781-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e9781-108">Level</span></span>|<span data-ttu-id="e9781-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="e9781-109">Verbose</span></span>|  
|<span data-ttu-id="e9781-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e9781-110">Channel</span></span>|<span data-ttu-id="e9781-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e9781-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e9781-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9781-112">Description</span></span>  
 <span data-ttu-id="e9781-113">Bir TransactionContextWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9781-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e9781-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e9781-114">Message</span></span>  
 <span data-ttu-id="e9781-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e9781-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e9781-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e9781-116">Details</span></span>  
  
|<span data-ttu-id="e9781-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e9781-117">Data Item Name</span></span>|<span data-ttu-id="e9781-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e9781-118">Data Item Type</span></span>|<span data-ttu-id="e9781-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9781-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e9781-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e9781-120">Activity</span></span>|<span data-ttu-id="e9781-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9781-121">xs:string</span></span>|<span data-ttu-id="e9781-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e9781-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e9781-123">displayName</span><span class="sxs-lookup"><span data-stu-id="e9781-123">DisplayName</span></span>|<span data-ttu-id="e9781-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9781-124">xs:string</span></span>|<span data-ttu-id="e9781-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e9781-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e9781-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e9781-126">InstanceId</span></span>|<span data-ttu-id="e9781-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9781-127">xs:string</span></span>|<span data-ttu-id="e9781-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="e9781-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e9781-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e9781-129">AppDomain</span></span>|<span data-ttu-id="e9781-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9781-130">xs:string</span></span>|<span data-ttu-id="e9781-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e9781-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
