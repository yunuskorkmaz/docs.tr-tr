---
description: 'Hakkında daha fazla bilgi edinin: 3557-TransactedReceiveScopeEndCommitFailed'
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 7865ae27e7ce5b3f13b3567f3f8aeebd6edf3fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777989"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="6f126-103">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="6f126-103">3557 - TransactedReceiveScopeEndCommitFailed</span></span>

## <a name="properties"></a><span data-ttu-id="6f126-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6f126-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f126-105">ID</span><span class="sxs-lookup"><span data-stu-id="6f126-105">ID</span></span>|<span data-ttu-id="6f126-106">3557</span><span class="sxs-lookup"><span data-stu-id="6f126-106">3557</span></span>|  
|<span data-ttu-id="6f126-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="6f126-107">Keywords</span></span>|<span data-ttu-id="6f126-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="6f126-108">WFServices</span></span>|  
|<span data-ttu-id="6f126-109">Level</span><span class="sxs-lookup"><span data-stu-id="6f126-109">Level</span></span>|<span data-ttu-id="6f126-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="6f126-110">Information</span></span>|  
|<span data-ttu-id="6f126-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="6f126-111">Channel</span></span>|<span data-ttu-id="6f126-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="6f126-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6f126-113">Description</span><span class="sxs-lookup"><span data-stu-id="6f126-113">Description</span></span>  

 <span data-ttu-id="6f126-114">Bir CommittableTransaction üzerinde Endcommıt çağrısının bir TransactionException olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f126-114">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6f126-115">İleti</span><span class="sxs-lookup"><span data-stu-id="6f126-115">Message</span></span>  

 <span data-ttu-id="6f126-116">ID = ' %1 ' olan CommittableTransaction üzerinde Endcommıt çağrısı şu iletiyle bir TransactionException oluşturdu: ' %2 '.</span><span class="sxs-lookup"><span data-stu-id="6f126-116">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6f126-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6f126-117">Details</span></span>  
  
|<span data-ttu-id="6f126-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="6f126-118">Data Item Name</span></span>|<span data-ttu-id="6f126-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="6f126-119">Data Item Type</span></span>|<span data-ttu-id="6f126-120">Description</span><span class="sxs-lookup"><span data-stu-id="6f126-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6f126-121">TransactionId</span><span class="sxs-lookup"><span data-stu-id="6f126-121">TransactionId</span></span>|<span data-ttu-id="6f126-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="6f126-122">xs:string</span></span>|<span data-ttu-id="6f126-123">CommittableTransaction kimliği.</span><span class="sxs-lookup"><span data-stu-id="6f126-123">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="6f126-124">Özel durum</span><span class="sxs-lookup"><span data-stu-id="6f126-124">Exception</span></span>|<span data-ttu-id="6f126-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="6f126-125">xs:string</span></span>|<span data-ttu-id="6f126-126">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="6f126-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="6f126-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6f126-127">AppDomain</span></span>|<span data-ttu-id="6f126-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="6f126-128">xs:string</span></span>|<span data-ttu-id="6f126-129">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6f126-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
