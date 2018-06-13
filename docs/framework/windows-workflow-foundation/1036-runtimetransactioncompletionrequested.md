---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510399"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="d0b31-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="d0b31-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="d0b31-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d0b31-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0b31-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="d0b31-104">ID</span></span>|<span data-ttu-id="d0b31-105">1036</span><span class="sxs-lookup"><span data-stu-id="d0b31-105">1036</span></span>|  
|<span data-ttu-id="d0b31-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="d0b31-106">Keywords</span></span>|<span data-ttu-id="d0b31-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d0b31-107">WFRuntime</span></span>|  
|<span data-ttu-id="d0b31-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d0b31-108">Level</span></span>|<span data-ttu-id="d0b31-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="d0b31-109">Verbose</span></span>|  
|<span data-ttu-id="d0b31-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d0b31-110">Channel</span></span>|<span data-ttu-id="d0b31-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d0b31-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d0b31-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0b31-112">Description</span></span>  
 <span data-ttu-id="d0b31-113">Etkinlik çalışma zamanı işlemin tamamlanmasından zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0b31-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d0b31-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d0b31-114">Message</span></span>  
 <span data-ttu-id="d0b31-115">Etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' çalışma zamanı TRANSACTION zamanlanmış.</span><span class="sxs-lookup"><span data-stu-id="d0b31-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d0b31-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d0b31-116">Details</span></span>  
  
|<span data-ttu-id="d0b31-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d0b31-117">Data Item Name</span></span>|<span data-ttu-id="d0b31-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d0b31-118">Data Item Type</span></span>|<span data-ttu-id="d0b31-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0b31-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d0b31-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="d0b31-120">Activity</span></span>|<span data-ttu-id="d0b31-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0b31-121">xs:string</span></span>|<span data-ttu-id="d0b31-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="d0b31-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d0b31-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="d0b31-123">DisplayName</span></span>|<span data-ttu-id="d0b31-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0b31-124">xs:string</span></span>|<span data-ttu-id="d0b31-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="d0b31-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d0b31-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="d0b31-126">InstanceId</span></span>|<span data-ttu-id="d0b31-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0b31-127">xs:string</span></span>|<span data-ttu-id="d0b31-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="d0b31-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d0b31-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d0b31-129">AppDomain</span></span>|<span data-ttu-id="d0b31-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0b31-130">xs:string</span></span>|<span data-ttu-id="d0b31-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d0b31-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
