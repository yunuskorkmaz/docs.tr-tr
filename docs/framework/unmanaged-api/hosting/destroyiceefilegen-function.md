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
ms.openlocfilehash: 37ff40e1c009b8e1e0509a4a3333d5a2a70bbfd2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159893"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="a899e-102">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="a899e-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="a899e-103">Yok eder bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="a899e-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="a899e-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a899e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a899e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a899e-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a899e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a899e-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="a899e-107">[in] `ICeeFileGen` Yok etmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="a899e-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a899e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a899e-108">Return Value</span></span>  
 <span data-ttu-id="a899e-109">Bu yöntem standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a899e-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a899e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a899e-110">Remarks</span></span>  
 <span data-ttu-id="a899e-111">`DestroyICeeFileGen` yok eder `ICeeFileGen` tarafından oluşturulan nesne [Createıceefilegen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="a899e-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a899e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a899e-112">Requirements</span></span>  
 <span data-ttu-id="a899e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a899e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a899e-114">**Üst bilgi:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="a899e-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="a899e-115">**Kitaplığı:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="a899e-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="a899e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a899e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a899e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a899e-117">See also</span></span>

- [<span data-ttu-id="a899e-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a899e-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
