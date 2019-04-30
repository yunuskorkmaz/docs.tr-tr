---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774380"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="f84db-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="f84db-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="f84db-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f84db-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f84db-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f84db-104">ID</span></span>|<span data-ttu-id="f84db-105">4202</span><span class="sxs-lookup"><span data-stu-id="f84db-105">4202</span></span>|  
|<span data-ttu-id="f84db-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f84db-106">Keywords</span></span>|<span data-ttu-id="f84db-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f84db-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f84db-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f84db-108">Level</span></span>|<span data-ttu-id="f84db-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="f84db-109">Verbose</span></span>|  
|<span data-ttu-id="f84db-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f84db-110">Channel</span></span>|<span data-ttu-id="f84db-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f84db-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f84db-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f84db-112">Description</span></span>  
 <span data-ttu-id="f84db-113">SQL komut yürütüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f84db-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f84db-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f84db-114">Message</span></span>  
 <span data-ttu-id="f84db-115">SQL komut yürütme başlatılıyor: %1</span><span class="sxs-lookup"><span data-stu-id="f84db-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="f84db-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f84db-116">Details</span></span>  
  
|<span data-ttu-id="f84db-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f84db-117">Data Item Name</span></span>|<span data-ttu-id="f84db-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f84db-118">Data Item Type</span></span>|<span data-ttu-id="f84db-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f84db-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f84db-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="f84db-120">SqlCommand</span></span>|<span data-ttu-id="f84db-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f84db-121">xs:string</span></span>|<span data-ttu-id="f84db-122">Yürütülen SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="f84db-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="f84db-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f84db-123">AppDomain</span></span>|<span data-ttu-id="f84db-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f84db-124">xs:string</span></span>|<span data-ttu-id="f84db-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f84db-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
