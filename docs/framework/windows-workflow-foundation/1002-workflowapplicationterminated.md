---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008661"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="b15aa-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="b15aa-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="b15aa-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b15aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b15aa-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b15aa-104">ID</span></span>|<span data-ttu-id="b15aa-105">1002</span><span class="sxs-lookup"><span data-stu-id="b15aa-105">1002</span></span>|  
|<span data-ttu-id="b15aa-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b15aa-106">Keywords</span></span>|<span data-ttu-id="b15aa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b15aa-107">WFRuntime</span></span>|  
|<span data-ttu-id="b15aa-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b15aa-108">Level</span></span>|<span data-ttu-id="b15aa-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="b15aa-109">Information</span></span>|  
|<span data-ttu-id="b15aa-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b15aa-110">Channel</span></span>|<span data-ttu-id="b15aa-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b15aa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b15aa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b15aa-112">Description</span></span>  
 <span data-ttu-id="b15aa-113">Faulted durumunda bir özel durum ile bir iş akışı uygulaması sonlandırıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b15aa-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b15aa-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b15aa-114">Message</span></span>  
 <span data-ttu-id="b15aa-115">WorkflowApplication ID: '%1' sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="b15aa-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="b15aa-116">Faulted durumunda bir özel durum ile tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b15aa-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b15aa-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b15aa-117">Details</span></span>  
  
|<span data-ttu-id="b15aa-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b15aa-118">Data Item Name</span></span>|<span data-ttu-id="b15aa-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b15aa-119">Data Item Type</span></span>|<span data-ttu-id="b15aa-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b15aa-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b15aa-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="b15aa-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="b15aa-122">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="b15aa-122">The workflow application id</span></span>|  
|<span data-ttu-id="b15aa-123">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="b15aa-123">Exception</span></span>|`xs:string`|<span data-ttu-id="b15aa-124">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b15aa-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="b15aa-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b15aa-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b15aa-126">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b15aa-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
