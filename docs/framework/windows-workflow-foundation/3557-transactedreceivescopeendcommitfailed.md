---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85e9456f6b4c1884b2e28671b304728135b6b1d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="9d2cb-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="9d2cb-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="9d2cb-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9d2cb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d2cb-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9d2cb-104">ID</span></span>|<span data-ttu-id="9d2cb-105">3557</span><span class="sxs-lookup"><span data-stu-id="9d2cb-105">3557</span></span>|  
|<span data-ttu-id="9d2cb-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9d2cb-106">Keywords</span></span>|<span data-ttu-id="9d2cb-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="9d2cb-107">WFServices</span></span>|  
|<span data-ttu-id="9d2cb-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9d2cb-108">Level</span></span>|<span data-ttu-id="9d2cb-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9d2cb-109">Information</span></span>|  
|<span data-ttu-id="9d2cb-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9d2cb-110">Channel</span></span>|<span data-ttu-id="9d2cb-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="9d2cb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9d2cb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d2cb-112">Description</span></span>  
 <span data-ttu-id="9d2cb-113">Bir CommittableTransaction üzerinde EndCommit çağrısı bir TransactionException belirtti gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d2cb-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9d2cb-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9d2cb-114">Message</span></span>  
 <span data-ttu-id="9d2cb-115">Kimliğine sahip CommittableTransaction üzerinde EndCommit çağrısı = '%1' TransactionException aşağıdaki iletiyle oluşturdu: '%2'.</span><span class="sxs-lookup"><span data-stu-id="9d2cb-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9d2cb-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9d2cb-116">Details</span></span>  
  
|<span data-ttu-id="9d2cb-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9d2cb-117">Data Item Name</span></span>|<span data-ttu-id="9d2cb-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9d2cb-118">Data Item Type</span></span>|<span data-ttu-id="9d2cb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d2cb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9d2cb-120">TransactionID</span><span class="sxs-lookup"><span data-stu-id="9d2cb-120">TransactionId</span></span>|<span data-ttu-id="9d2cb-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="9d2cb-121">xs:string</span></span>|<span data-ttu-id="9d2cb-122">CommittableTransaction kimliği.</span><span class="sxs-lookup"><span data-stu-id="9d2cb-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="9d2cb-123">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="9d2cb-123">Exception</span></span>|<span data-ttu-id="9d2cb-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="9d2cb-124">xs:string</span></span>|<span data-ttu-id="9d2cb-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9d2cb-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="9d2cb-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9d2cb-126">AppDomain</span></span>|<span data-ttu-id="9d2cb-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="9d2cb-127">xs:string</span></span>|<span data-ttu-id="9d2cb-128">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9d2cb-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
