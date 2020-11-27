---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 0d6326889077e36ad49aa6267ae7285849c6818d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275872"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="45452-102">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="45452-102">4201 - EndSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="45452-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="45452-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45452-104">ID</span><span class="sxs-lookup"><span data-stu-id="45452-104">ID</span></span>|<span data-ttu-id="45452-105">4201</span><span class="sxs-lookup"><span data-stu-id="45452-105">4201</span></span>|  
|<span data-ttu-id="45452-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="45452-106">Keywords</span></span>|<span data-ttu-id="45452-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="45452-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="45452-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="45452-108">Level</span></span>|<span data-ttu-id="45452-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="45452-109">Verbose</span></span>|  
|<span data-ttu-id="45452-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="45452-110">Channel</span></span>|<span data-ttu-id="45452-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="45452-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="45452-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45452-112">Description</span></span>  

 <span data-ttu-id="45452-113">Bir SQL komutunun yürütmeyi bitirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="45452-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="45452-114">İleti</span><span class="sxs-lookup"><span data-stu-id="45452-114">Message</span></span>  

 <span data-ttu-id="45452-115">SQL komutunun yürütülmesini sonlandır: %1</span><span class="sxs-lookup"><span data-stu-id="45452-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="45452-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="45452-116">Details</span></span>  
  
|<span data-ttu-id="45452-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="45452-117">Data Item Name</span></span>|<span data-ttu-id="45452-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="45452-118">Data Item Type</span></span>|<span data-ttu-id="45452-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45452-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="45452-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="45452-120">SqlCommand</span></span>|<span data-ttu-id="45452-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="45452-121">xs:string</span></span>|<span data-ttu-id="45452-122">Yürütülen SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="45452-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="45452-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="45452-123">AppDomain</span></span>|<span data-ttu-id="45452-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="45452-124">xs:string</span></span>|<span data-ttu-id="45452-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="45452-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
