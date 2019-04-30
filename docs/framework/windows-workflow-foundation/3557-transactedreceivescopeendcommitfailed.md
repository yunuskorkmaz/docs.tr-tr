---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774458"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="b071d-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="b071d-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="b071d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b071d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b071d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b071d-104">ID</span></span>|<span data-ttu-id="b071d-105">3557</span><span class="sxs-lookup"><span data-stu-id="b071d-105">3557</span></span>|  
|<span data-ttu-id="b071d-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b071d-106">Keywords</span></span>|<span data-ttu-id="b071d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b071d-107">WFServices</span></span>|  
|<span data-ttu-id="b071d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b071d-108">Level</span></span>|<span data-ttu-id="b071d-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="b071d-109">Information</span></span>|  
|<span data-ttu-id="b071d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b071d-110">Channel</span></span>|<span data-ttu-id="b071d-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="b071d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b071d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b071d-112">Description</span></span>  
 <span data-ttu-id="b071d-113">Bir CommittableTransaction üzerinde EndCommit çağrısı bir TransactionException oluşturdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b071d-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b071d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b071d-114">Message</span></span>  
 <span data-ttu-id="b071d-115">CommittableTransaction kimliğiyle şirket EndCommit çağrısı = '%1', şu iletiyle bir TransactionException oluşturdu: '%2'.</span><span class="sxs-lookup"><span data-stu-id="b071d-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b071d-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b071d-116">Details</span></span>  
  
|<span data-ttu-id="b071d-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b071d-117">Data Item Name</span></span>|<span data-ttu-id="b071d-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b071d-118">Data Item Type</span></span>|<span data-ttu-id="b071d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b071d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b071d-120">TransactionID</span><span class="sxs-lookup"><span data-stu-id="b071d-120">TransactionId</span></span>|<span data-ttu-id="b071d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b071d-121">xs:string</span></span>|<span data-ttu-id="b071d-122">CommittableTransaction kimliği.</span><span class="sxs-lookup"><span data-stu-id="b071d-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="b071d-123">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="b071d-123">Exception</span></span>|<span data-ttu-id="b071d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b071d-124">xs:string</span></span>|<span data-ttu-id="b071d-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b071d-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="b071d-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b071d-126">AppDomain</span></span>|<span data-ttu-id="b071d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="b071d-127">xs:string</span></span>|<span data-ttu-id="b071d-128">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b071d-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
