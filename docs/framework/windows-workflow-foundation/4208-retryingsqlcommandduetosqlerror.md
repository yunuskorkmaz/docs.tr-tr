---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774302"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="8f0cd-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="8f0cd-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="8f0cd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8f0cd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f0cd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8f0cd-104">ID</span></span>|<span data-ttu-id="8f0cd-105">4208</span><span class="sxs-lookup"><span data-stu-id="8f0cd-105">4208</span></span>|  
|<span data-ttu-id="8f0cd-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8f0cd-106">Keywords</span></span>|<span data-ttu-id="8f0cd-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="8f0cd-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="8f0cd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8f0cd-108">Level</span></span>|<span data-ttu-id="8f0cd-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="8f0cd-109">Information</span></span>|  
|<span data-ttu-id="8f0cd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8f0cd-110">Channel</span></span>|<span data-ttu-id="8f0cd-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8f0cd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8f0cd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f0cd-112">Description</span></span>  
 <span data-ttu-id="8f0cd-113">SQL sağlayıcı bir SQL komutunu SQL hatası nedeniyle yeniden deneniyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f0cd-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8f0cd-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8f0cd-114">Message</span></span>  
 <span data-ttu-id="8f0cd-115">Bir SQL komutunu SQL hata numarası: %1'nedeniyle yeniden deneniyor.</span><span class="sxs-lookup"><span data-stu-id="8f0cd-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8f0cd-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8f0cd-116">Details</span></span>  
  
|<span data-ttu-id="8f0cd-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8f0cd-117">Data Item Name</span></span>|<span data-ttu-id="8f0cd-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8f0cd-118">Data Item Type</span></span>|<span data-ttu-id="8f0cd-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f0cd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8f0cd-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="8f0cd-120">ErrorNumber</span></span>|<span data-ttu-id="8f0cd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8f0cd-121">xs:string</span></span>|<span data-ttu-id="8f0cd-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="8f0cd-122">The SQL error number.</span></span>|  
|<span data-ttu-id="8f0cd-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8f0cd-123">AppDomain</span></span>|<span data-ttu-id="8f0cd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8f0cd-124">xs:string</span></span>|<span data-ttu-id="8f0cd-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8f0cd-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
