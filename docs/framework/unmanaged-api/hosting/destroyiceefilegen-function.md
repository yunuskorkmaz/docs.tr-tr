---
title: DestroyICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e108dd925432b8ec193863de4cb085dad50cdd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429079"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="fadc1-102">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="fadc1-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="fadc1-103">Bozar bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fadc1-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="fadc1-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fadc1-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fadc1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fadc1-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fadc1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fadc1-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="fadc1-107">[in] `ICeeFileGen` Nesne yok.</span><span class="sxs-lookup"><span data-stu-id="fadc1-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fadc1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fadc1-108">Return Value</span></span>  
 <span data-ttu-id="fadc1-109">Bu yöntem standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="fadc1-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fadc1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fadc1-110">Remarks</span></span>  
 <span data-ttu-id="fadc1-111">`DestroyICeeFileGen` bozar `ICeeFileGen` tarafından oluşturulan nesne [Createıceefilegen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="fadc1-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fadc1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fadc1-112">Requirements</span></span>  
 <span data-ttu-id="fadc1-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fadc1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fadc1-114">**Başlık:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="fadc1-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="fadc1-115">**Kitaplığı:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="fadc1-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="fadc1-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fadc1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fadc1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fadc1-117">See Also</span></span>  
 [<span data-ttu-id="fadc1-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fadc1-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
