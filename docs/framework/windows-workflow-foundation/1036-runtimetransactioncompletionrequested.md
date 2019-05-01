---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924845"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="c6128-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="c6128-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="c6128-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c6128-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6128-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c6128-104">ID</span></span>|<span data-ttu-id="c6128-105">1036</span><span class="sxs-lookup"><span data-stu-id="c6128-105">1036</span></span>|  
|<span data-ttu-id="c6128-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c6128-106">Keywords</span></span>|<span data-ttu-id="c6128-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c6128-107">WFRuntime</span></span>|  
|<span data-ttu-id="c6128-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c6128-108">Level</span></span>|<span data-ttu-id="c6128-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="c6128-109">Verbose</span></span>|  
|<span data-ttu-id="c6128-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c6128-110">Channel</span></span>|<span data-ttu-id="c6128-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c6128-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c6128-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6128-112">Description</span></span>  
 <span data-ttu-id="c6128-113">Bir etkinliğin çalışma zamanı işlemin tamamlanmasından planladı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6128-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c6128-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c6128-114">Message</span></span>  
 <span data-ttu-id="c6128-115">Etkinliği '%1', DisplayName: '%2', InstanceId: '%3', çalışma zamanı TRANSACTION zamanlanmış.</span><span class="sxs-lookup"><span data-stu-id="c6128-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c6128-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c6128-116">Details</span></span>  
  
|<span data-ttu-id="c6128-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c6128-117">Data Item Name</span></span>|<span data-ttu-id="c6128-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c6128-118">Data Item Type</span></span>|<span data-ttu-id="c6128-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6128-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c6128-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="c6128-120">Activity</span></span>|<span data-ttu-id="c6128-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6128-121">xs:string</span></span>|<span data-ttu-id="c6128-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="c6128-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c6128-123">displayName</span><span class="sxs-lookup"><span data-stu-id="c6128-123">DisplayName</span></span>|<span data-ttu-id="c6128-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6128-124">xs:string</span></span>|<span data-ttu-id="c6128-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c6128-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c6128-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c6128-126">InstanceId</span></span>|<span data-ttu-id="c6128-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6128-127">xs:string</span></span>|<span data-ttu-id="c6128-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="c6128-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c6128-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c6128-129">AppDomain</span></span>|<span data-ttu-id="c6128-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6128-130">xs:string</span></span>|<span data-ttu-id="c6128-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c6128-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
