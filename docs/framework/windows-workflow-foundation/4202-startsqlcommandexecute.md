---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: d3f27c6ed28efe9d099dcedfc676b839ae9b1dee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275846"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="27fb8-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="27fb8-102">4202 - StartSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="27fb8-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="27fb8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27fb8-104">ID</span><span class="sxs-lookup"><span data-stu-id="27fb8-104">ID</span></span>|<span data-ttu-id="27fb8-105">4202</span><span class="sxs-lookup"><span data-stu-id="27fb8-105">4202</span></span>|  
|<span data-ttu-id="27fb8-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="27fb8-106">Keywords</span></span>|<span data-ttu-id="27fb8-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="27fb8-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="27fb8-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="27fb8-108">Level</span></span>|<span data-ttu-id="27fb8-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="27fb8-109">Verbose</span></span>|  
|<span data-ttu-id="27fb8-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="27fb8-110">Channel</span></span>|<span data-ttu-id="27fb8-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="27fb8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="27fb8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27fb8-112">Description</span></span>  

 <span data-ttu-id="27fb8-113">Bir SQL komutunun yürütüldüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="27fb8-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="27fb8-114">İleti</span><span class="sxs-lookup"><span data-stu-id="27fb8-114">Message</span></span>  

 <span data-ttu-id="27fb8-115">SQL komutu yürütme başlatılıyor: %1</span><span class="sxs-lookup"><span data-stu-id="27fb8-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="27fb8-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="27fb8-116">Details</span></span>  
  
|<span data-ttu-id="27fb8-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="27fb8-117">Data Item Name</span></span>|<span data-ttu-id="27fb8-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="27fb8-118">Data Item Type</span></span>|<span data-ttu-id="27fb8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27fb8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="27fb8-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="27fb8-120">SqlCommand</span></span>|<span data-ttu-id="27fb8-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="27fb8-121">xs:string</span></span>|<span data-ttu-id="27fb8-122">Yürütülen SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="27fb8-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="27fb8-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="27fb8-123">AppDomain</span></span>|<span data-ttu-id="27fb8-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="27fb8-124">xs:string</span></span>|<span data-ttu-id="27fb8-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="27fb8-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
