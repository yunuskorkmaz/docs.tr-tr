---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510085"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="700ee-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="700ee-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="700ee-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="700ee-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="700ee-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="700ee-104">ID</span></span>|<span data-ttu-id="700ee-105">1002</span><span class="sxs-lookup"><span data-stu-id="700ee-105">1002</span></span>|  
|<span data-ttu-id="700ee-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="700ee-106">Keywords</span></span>|<span data-ttu-id="700ee-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="700ee-107">WFRuntime</span></span>|  
|<span data-ttu-id="700ee-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="700ee-108">Level</span></span>|<span data-ttu-id="700ee-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="700ee-109">Information</span></span>|  
|<span data-ttu-id="700ee-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="700ee-110">Channel</span></span>|<span data-ttu-id="700ee-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="700ee-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="700ee-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="700ee-112">Description</span></span>  
 <span data-ttu-id="700ee-113">Bir iş akışı uygulaması Faulted durumunda bir özel durum ile sona erdi gösterir.</span><span class="sxs-lookup"><span data-stu-id="700ee-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="700ee-114">İleti</span><span class="sxs-lookup"><span data-stu-id="700ee-114">Message</span></span>  
 <span data-ttu-id="700ee-115">WorkflowApplication kimliği: '%1' sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="700ee-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="700ee-116">Faulted durumunda bir özel durum ile tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="700ee-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="700ee-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="700ee-117">Details</span></span>  
  
|<span data-ttu-id="700ee-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="700ee-118">Data Item Name</span></span>|<span data-ttu-id="700ee-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="700ee-119">Data Item Type</span></span>|<span data-ttu-id="700ee-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="700ee-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="700ee-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="700ee-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="700ee-122">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="700ee-122">The workflow application id</span></span>|  
|<span data-ttu-id="700ee-123">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="700ee-123">Exception</span></span>|`xs:string`|<span data-ttu-id="700ee-124">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="700ee-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="700ee-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="700ee-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="700ee-126">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="700ee-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
