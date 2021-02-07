---
description: 'Daha fazla bilgi edinin: IValidator arabirimi'
title: IValidator Arabirimi
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
ms.openlocfilehash: bc18b68d0e9a0e978789ab92afaed28751925870
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680102"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="93f29-103">IValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93f29-103">IValidator Interface</span></span>

<span data-ttu-id="93f29-104">Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="93f29-104">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93f29-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="93f29-105">Methods</span></span>  
  
|<span data-ttu-id="93f29-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="93f29-106">Method</span></span>|<span data-ttu-id="93f29-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93f29-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="93f29-108">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="93f29-108">Validate</span></span>|<span data-ttu-id="93f29-109">Belirtilen PE veya Microsoft ara dili (MSIL) dosyasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="93f29-109">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="93f29-110">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="93f29-110">FormatEventInfo</span></span>|<span data-ttu-id="93f29-111">Belirtilen doğrulama hatasına karşılık gelen hata iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="93f29-111">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93f29-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93f29-112">Requirements</span></span>  

 <span data-ttu-id="93f29-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f29-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f29-114">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="93f29-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="93f29-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="93f29-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93f29-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f29-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f29-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93f29-117">See also</span></span>

- [<span data-ttu-id="93f29-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="93f29-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="93f29-119">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="93f29-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
