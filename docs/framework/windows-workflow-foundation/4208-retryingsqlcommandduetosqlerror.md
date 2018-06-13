---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511606"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="f4363-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="f4363-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="f4363-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f4363-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4363-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f4363-104">ID</span></span>|<span data-ttu-id="f4363-105">4208</span><span class="sxs-lookup"><span data-stu-id="f4363-105">4208</span></span>|  
|<span data-ttu-id="f4363-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f4363-106">Keywords</span></span>|<span data-ttu-id="f4363-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f4363-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f4363-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f4363-108">Level</span></span>|<span data-ttu-id="f4363-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f4363-109">Information</span></span>|  
|<span data-ttu-id="f4363-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f4363-110">Channel</span></span>|<span data-ttu-id="f4363-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f4363-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4363-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4363-112">Description</span></span>  
 <span data-ttu-id="f4363-113">SQL sağlayıcısı bir SQL komutu bir SQL hatası nedeniyle yeniden deneniyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4363-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4363-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f4363-114">Message</span></span>  
 <span data-ttu-id="f4363-115">Bir SQL komutu SQL hata numarası %1 nedeniyle yeniden deneniyor.</span><span class="sxs-lookup"><span data-stu-id="f4363-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4363-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f4363-116">Details</span></span>  
  
|<span data-ttu-id="f4363-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f4363-117">Data Item Name</span></span>|<span data-ttu-id="f4363-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f4363-118">Data Item Type</span></span>|<span data-ttu-id="f4363-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4363-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4363-120">HataNumarası</span><span class="sxs-lookup"><span data-stu-id="f4363-120">ErrorNumber</span></span>|<span data-ttu-id="f4363-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="f4363-121">xs:string</span></span>|<span data-ttu-id="f4363-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="f4363-122">The SQL error number.</span></span>|  
|<span data-ttu-id="f4363-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f4363-123">AppDomain</span></span>|<span data-ttu-id="f4363-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f4363-124">xs:string</span></span>|<span data-ttu-id="f4363-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f4363-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
