---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: b763e087d8ead2bcc0fadd1d0223ae1bd58c9fd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774315"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="5c44c-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="5c44c-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="5c44c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5c44c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c44c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="5c44c-104">ID</span></span>|<span data-ttu-id="5c44c-105">4207</span><span class="sxs-lookup"><span data-stu-id="5c44c-105">4207</span></span>|  
|<span data-ttu-id="5c44c-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5c44c-106">Keywords</span></span>|<span data-ttu-id="5c44c-107">Kota, WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5c44c-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="5c44c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5c44c-108">Level</span></span>|<span data-ttu-id="5c44c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="5c44c-109">Information</span></span>|  
|<span data-ttu-id="5c44c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5c44c-110">Channel</span></span>|<span data-ttu-id="5c44c-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5c44c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5c44c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c44c-112">Description</span></span>  
 <span data-ttu-id="5c44c-113">Yeniden deneme sayısı gerçekleştirilmiş olarak bir SQL komutu yeniden deneniyor ayarlama SQL sağlayıcısı vererek gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c44c-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5c44c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="5c44c-114">Message</span></span>  
 <span data-ttu-id="5c44c-115">En fazla yeniden deneme sayısı arttıkça SQL komutunu yeniden deneniyor yukarı vererek yapıldı.</span><span class="sxs-lookup"><span data-stu-id="5c44c-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5c44c-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5c44c-116">Details</span></span>  
  
|<span data-ttu-id="5c44c-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5c44c-117">Data Item Name</span></span>|<span data-ttu-id="5c44c-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5c44c-118">Data Item Type</span></span>|<span data-ttu-id="5c44c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c44c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5c44c-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5c44c-120">AppDomain</span></span>|<span data-ttu-id="5c44c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5c44c-121">xs:string</span></span>|<span data-ttu-id="5c44c-122">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5c44c-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
