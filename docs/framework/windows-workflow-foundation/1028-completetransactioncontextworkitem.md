---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 806a437822cef8802a2bef6a54f924f84c88ef60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008817"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="07aaf-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="07aaf-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="07aaf-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="07aaf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07aaf-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="07aaf-104">ID</span></span>|<span data-ttu-id="07aaf-105">1028</span><span class="sxs-lookup"><span data-stu-id="07aaf-105">1028</span></span>|  
|<span data-ttu-id="07aaf-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="07aaf-106">Keywords</span></span>|<span data-ttu-id="07aaf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="07aaf-107">WFRuntime</span></span>|  
|<span data-ttu-id="07aaf-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="07aaf-108">Level</span></span>|<span data-ttu-id="07aaf-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="07aaf-109">Verbose</span></span>|  
|<span data-ttu-id="07aaf-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="07aaf-110">Channel</span></span>|<span data-ttu-id="07aaf-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="07aaf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="07aaf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07aaf-112">Description</span></span>  
 <span data-ttu-id="07aaf-113">Bir TransactionContextWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="07aaf-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="07aaf-114">İleti</span><span class="sxs-lookup"><span data-stu-id="07aaf-114">Message</span></span>  
 <span data-ttu-id="07aaf-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem tamamlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="07aaf-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="07aaf-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="07aaf-116">Details</span></span>  
  
|<span data-ttu-id="07aaf-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="07aaf-117">Data Item Name</span></span>|<span data-ttu-id="07aaf-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="07aaf-118">Data Item Type</span></span>|<span data-ttu-id="07aaf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07aaf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="07aaf-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="07aaf-120">Activity</span></span>|<span data-ttu-id="07aaf-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="07aaf-121">xs:string</span></span>|<span data-ttu-id="07aaf-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="07aaf-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="07aaf-123">displayName</span><span class="sxs-lookup"><span data-stu-id="07aaf-123">DisplayName</span></span>|<span data-ttu-id="07aaf-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="07aaf-124">xs:string</span></span>|<span data-ttu-id="07aaf-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="07aaf-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="07aaf-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="07aaf-126">InstanceId</span></span>|<span data-ttu-id="07aaf-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="07aaf-127">xs:string</span></span>|<span data-ttu-id="07aaf-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="07aaf-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="07aaf-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="07aaf-129">AppDomain</span></span>|<span data-ttu-id="07aaf-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="07aaf-130">xs:string</span></span>|<span data-ttu-id="07aaf-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="07aaf-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
