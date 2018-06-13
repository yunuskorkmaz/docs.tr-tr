---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510357"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="7d6e7-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="7d6e7-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="7d6e7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7d6e7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d6e7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="7d6e7-104">ID</span></span>|<span data-ttu-id="7d6e7-105">4202</span><span class="sxs-lookup"><span data-stu-id="7d6e7-105">4202</span></span>|  
|<span data-ttu-id="7d6e7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="7d6e7-106">Keywords</span></span>|<span data-ttu-id="7d6e7-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="7d6e7-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="7d6e7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="7d6e7-108">Level</span></span>|<span data-ttu-id="7d6e7-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="7d6e7-109">Verbose</span></span>|  
|<span data-ttu-id="7d6e7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="7d6e7-110">Channel</span></span>|<span data-ttu-id="7d6e7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="7d6e7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7d6e7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d6e7-112">Description</span></span>  
 <span data-ttu-id="7d6e7-113">Bir SQL komutu yürütülen gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d6e7-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7d6e7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="7d6e7-114">Message</span></span>  
 <span data-ttu-id="7d6e7-115">SQL komutu yürütme başlangıç: %1</span><span class="sxs-lookup"><span data-stu-id="7d6e7-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="7d6e7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7d6e7-116">Details</span></span>  
  
|<span data-ttu-id="7d6e7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7d6e7-117">Data Item Name</span></span>|<span data-ttu-id="7d6e7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7d6e7-118">Data Item Type</span></span>|<span data-ttu-id="7d6e7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d6e7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7d6e7-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="7d6e7-120">SqlCommand</span></span>|<span data-ttu-id="7d6e7-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="7d6e7-121">xs:string</span></span>|<span data-ttu-id="7d6e7-122">Yürütülen SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="7d6e7-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="7d6e7-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7d6e7-123">AppDomain</span></span>|<span data-ttu-id="7d6e7-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="7d6e7-124">xs:string</span></span>|<span data-ttu-id="7d6e7-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7d6e7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
