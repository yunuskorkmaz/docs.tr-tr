---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 4a4979047481687ef0d5c9d5891dec8f2826beed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263665"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="f4616-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="f4616-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>

## <a name="properties"></a><span data-ttu-id="f4616-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f4616-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4616-104">ID</span><span class="sxs-lookup"><span data-stu-id="f4616-104">ID</span></span>|<span data-ttu-id="f4616-105">3557</span><span class="sxs-lookup"><span data-stu-id="f4616-105">3557</span></span>|  
|<span data-ttu-id="f4616-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f4616-106">Keywords</span></span>|<span data-ttu-id="f4616-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="f4616-107">WFServices</span></span>|  
|<span data-ttu-id="f4616-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f4616-108">Level</span></span>|<span data-ttu-id="f4616-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="f4616-109">Information</span></span>|  
|<span data-ttu-id="f4616-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f4616-110">Channel</span></span>|<span data-ttu-id="f4616-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f4616-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4616-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4616-112">Description</span></span>  

 <span data-ttu-id="f4616-113">Bir CommittableTransaction üzerinde Endcommıt çağrısının bir TransactionException olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4616-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4616-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f4616-114">Message</span></span>  

 <span data-ttu-id="f4616-115">ID = ' %1 ' olan CommittableTransaction üzerinde Endcommıt çağrısı şu iletiyle bir TransactionException oluşturdu: ' %2 '.</span><span class="sxs-lookup"><span data-stu-id="f4616-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4616-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f4616-116">Details</span></span>  
  
|<span data-ttu-id="f4616-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f4616-117">Data Item Name</span></span>|<span data-ttu-id="f4616-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f4616-118">Data Item Type</span></span>|<span data-ttu-id="f4616-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4616-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4616-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="f4616-120">TransactionId</span></span>|<span data-ttu-id="f4616-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="f4616-121">xs:string</span></span>|<span data-ttu-id="f4616-122">CommittableTransaction kimliği.</span><span class="sxs-lookup"><span data-stu-id="f4616-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="f4616-123">Özel durum</span><span class="sxs-lookup"><span data-stu-id="f4616-123">Exception</span></span>|<span data-ttu-id="f4616-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f4616-124">xs:string</span></span>|<span data-ttu-id="f4616-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="f4616-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="f4616-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f4616-126">AppDomain</span></span>|<span data-ttu-id="f4616-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="f4616-127">xs:string</span></span>|<span data-ttu-id="f4616-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f4616-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
