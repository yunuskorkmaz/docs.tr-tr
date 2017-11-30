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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1f9f1066f1948411d584a2dee1af2129aa3a103
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="8dd26-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="8dd26-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="8dd26-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8dd26-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8dd26-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8dd26-104">ID</span></span>|<span data-ttu-id="8dd26-105">3557</span><span class="sxs-lookup"><span data-stu-id="8dd26-105">3557</span></span>|  
|<span data-ttu-id="8dd26-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="8dd26-106">Keywords</span></span>|<span data-ttu-id="8dd26-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8dd26-107">WFServices</span></span>|  
|<span data-ttu-id="8dd26-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8dd26-108">Level</span></span>|<span data-ttu-id="8dd26-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="8dd26-109">Information</span></span>|  
|<span data-ttu-id="8dd26-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8dd26-110">Channel</span></span>|<span data-ttu-id="8dd26-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="8dd26-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8dd26-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dd26-112">Description</span></span>  
 <span data-ttu-id="8dd26-113">Bir CommittableTransaction üzerinde EndCommit çağrısı bir TransactionException belirtti gösterir.</span><span class="sxs-lookup"><span data-stu-id="8dd26-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8dd26-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8dd26-114">Message</span></span>  
 <span data-ttu-id="8dd26-115">Kimliğine sahip CommittableTransaction üzerinde EndCommit çağrısı = '%1' TransactionException aşağıdaki iletiyle oluşturdu: '%2'.</span><span class="sxs-lookup"><span data-stu-id="8dd26-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8dd26-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8dd26-116">Details</span></span>  
  
|<span data-ttu-id="8dd26-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8dd26-117">Data Item Name</span></span>|<span data-ttu-id="8dd26-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8dd26-118">Data Item Type</span></span>|<span data-ttu-id="8dd26-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dd26-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8dd26-120">TransactionID</span><span class="sxs-lookup"><span data-stu-id="8dd26-120">TransactionId</span></span>|<span data-ttu-id="8dd26-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="8dd26-121">xs:string</span></span>|<span data-ttu-id="8dd26-122">CommittableTransaction kimliği.</span><span class="sxs-lookup"><span data-stu-id="8dd26-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="8dd26-123">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="8dd26-123">Exception</span></span>|<span data-ttu-id="8dd26-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="8dd26-124">xs:string</span></span>|<span data-ttu-id="8dd26-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="8dd26-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="8dd26-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8dd26-126">AppDomain</span></span>|<span data-ttu-id="8dd26-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="8dd26-127">xs:string</span></span>|<span data-ttu-id="8dd26-128">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8dd26-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
