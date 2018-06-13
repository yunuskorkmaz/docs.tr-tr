---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512167"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="219a2-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="219a2-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="219a2-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="219a2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="219a2-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="219a2-104">ID</span></span>|<span data-ttu-id="219a2-105">3557</span><span class="sxs-lookup"><span data-stu-id="219a2-105">3557</span></span>|  
|<span data-ttu-id="219a2-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="219a2-106">Keywords</span></span>|<span data-ttu-id="219a2-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="219a2-107">WFServices</span></span>|  
|<span data-ttu-id="219a2-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="219a2-108">Level</span></span>|<span data-ttu-id="219a2-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="219a2-109">Information</span></span>|  
|<span data-ttu-id="219a2-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="219a2-110">Channel</span></span>|<span data-ttu-id="219a2-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="219a2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="219a2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="219a2-112">Description</span></span>  
 <span data-ttu-id="219a2-113">Bir CommittableTransaction üzerinde EndCommit çağrısı bir TransactionException belirtti gösterir.</span><span class="sxs-lookup"><span data-stu-id="219a2-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="219a2-114">İleti</span><span class="sxs-lookup"><span data-stu-id="219a2-114">Message</span></span>  
 <span data-ttu-id="219a2-115">Kimliğine sahip CommittableTransaction üzerinde EndCommit çağrısı = '%1' TransactionException aşağıdaki iletiyle oluşturdu: '%2'.</span><span class="sxs-lookup"><span data-stu-id="219a2-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="219a2-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="219a2-116">Details</span></span>  
  
|<span data-ttu-id="219a2-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="219a2-117">Data Item Name</span></span>|<span data-ttu-id="219a2-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="219a2-118">Data Item Type</span></span>|<span data-ttu-id="219a2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="219a2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="219a2-120">TransactionID</span><span class="sxs-lookup"><span data-stu-id="219a2-120">TransactionId</span></span>|<span data-ttu-id="219a2-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="219a2-121">xs:string</span></span>|<span data-ttu-id="219a2-122">CommittableTransaction kimliği.</span><span class="sxs-lookup"><span data-stu-id="219a2-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="219a2-123">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="219a2-123">Exception</span></span>|<span data-ttu-id="219a2-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="219a2-124">xs:string</span></span>|<span data-ttu-id="219a2-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="219a2-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="219a2-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="219a2-126">AppDomain</span></span>|<span data-ttu-id="219a2-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="219a2-127">xs:string</span></span>|<span data-ttu-id="219a2-128">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="219a2-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
