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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159893"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="9db82-102">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="9db82-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="9db82-103">Yok eder bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="9db82-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="9db82-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9db82-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db82-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9db82-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9db82-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9db82-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="9db82-107">[in] `ICeeFileGen` Yok etmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="9db82-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9db82-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9db82-108">Return Value</span></span>  
 <span data-ttu-id="9db82-109">Bu yöntem standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="9db82-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9db82-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9db82-110">Remarks</span></span>  
 `DestroyICeeFileGen` <span data-ttu-id="9db82-111">yok eder `ICeeFileGen` tarafından oluşturulan nesne [Createıceefilegen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="9db82-111">destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db82-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9db82-112">Requirements</span></span>  
 <span data-ttu-id="9db82-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9db82-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9db82-114">**Üst bilgi:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="9db82-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="9db82-115">**Kitaplığı:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="9db82-115">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="9db82-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9db82-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9db82-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9db82-117">See also</span></span>

- [<span data-ttu-id="9db82-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9db82-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
