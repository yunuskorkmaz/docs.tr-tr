---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f307ad5689602b030c609a51f6834bdbb0ec4f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717722"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="4d0c6-102">IValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d0c6-102">IValidator Interface</span></span>
<span data-ttu-id="4d0c6-103">Taşınabilir yürütülebilir (PE) görüntüleri doğrulanıyor ve doğrulama hatalarını raporlama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d0c6-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d0c6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d0c6-104">Methods</span></span>  
  
|<span data-ttu-id="4d0c6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4d0c6-105">Method</span></span>|<span data-ttu-id="4d0c6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d0c6-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4d0c6-107">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="4d0c6-107">Validate</span></span>|<span data-ttu-id="4d0c6-108">Belirtilen PE veya Microsoft Ara dili (MSIL) dosya doğrular.</span><span class="sxs-lookup"><span data-stu-id="4d0c6-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="4d0c6-109">Formateventınfo</span><span class="sxs-lookup"><span data-stu-id="4d0c6-109">FormatEventInfo</span></span>|<span data-ttu-id="4d0c6-110">Belirtilen doğrulama hatası için karşılık gelen hata iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="4d0c6-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d0c6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d0c6-111">Requirements</span></span>  
 <span data-ttu-id="4d0c6-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d0c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d0c6-113">**Üst bilgi:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="4d0c6-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="4d0c6-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4d0c6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d0c6-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d0c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0c6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d0c6-116">See also</span></span>
- [<span data-ttu-id="4d0c6-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4d0c6-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4d0c6-118">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="4d0c6-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
