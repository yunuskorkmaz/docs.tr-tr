---
description: 'Hakkında daha fazla bilgi edinin: 4201-Endsqlcommandexyürütüldüğünde'
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: e0b98e8da5a0a284bfa55e97f5dde25a2ce42b42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755375"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="14a87-103">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="14a87-103">4201 - EndSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="14a87-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="14a87-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14a87-105">ID</span><span class="sxs-lookup"><span data-stu-id="14a87-105">ID</span></span>|<span data-ttu-id="14a87-106">4201</span><span class="sxs-lookup"><span data-stu-id="14a87-106">4201</span></span>|  
|<span data-ttu-id="14a87-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="14a87-107">Keywords</span></span>|<span data-ttu-id="14a87-108">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="14a87-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="14a87-109">Level</span><span class="sxs-lookup"><span data-stu-id="14a87-109">Level</span></span>|<span data-ttu-id="14a87-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="14a87-110">Verbose</span></span>|  
|<span data-ttu-id="14a87-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="14a87-111">Channel</span></span>|<span data-ttu-id="14a87-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="14a87-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14a87-113">Description</span><span class="sxs-lookup"><span data-stu-id="14a87-113">Description</span></span>  

 <span data-ttu-id="14a87-114">Bir SQL komutunun yürütmeyi bitirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="14a87-114">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14a87-115">İleti</span><span class="sxs-lookup"><span data-stu-id="14a87-115">Message</span></span>  

 <span data-ttu-id="14a87-116">SQL komutunun yürütülmesini sonlandır: %1</span><span class="sxs-lookup"><span data-stu-id="14a87-116">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="14a87-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="14a87-117">Details</span></span>  
  
|<span data-ttu-id="14a87-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="14a87-118">Data Item Name</span></span>|<span data-ttu-id="14a87-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="14a87-119">Data Item Type</span></span>|<span data-ttu-id="14a87-120">Description</span><span class="sxs-lookup"><span data-stu-id="14a87-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14a87-121">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="14a87-121">SqlCommand</span></span>|<span data-ttu-id="14a87-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="14a87-122">xs:string</span></span>|<span data-ttu-id="14a87-123">Yürütülen SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="14a87-123">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="14a87-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14a87-124">AppDomain</span></span>|<span data-ttu-id="14a87-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="14a87-125">xs:string</span></span>|<span data-ttu-id="14a87-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="14a87-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
