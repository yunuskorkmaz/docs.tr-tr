---
title: StrongNameFreeBuffer İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bfc6491a1d18c81a44a7d9c5084f744c9b76281
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072587"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="2e032-102">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="2e032-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="2e032-103">Önceki bir tanımlayıcı ad işlev çağrısı ile ayrıldı bellek serbest bırakma [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), veya [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="2e032-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="2e032-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="2e032-104">This function has been deprecated.</span></span> <span data-ttu-id="2e032-105">Kullanım [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="2e032-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e032-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e032-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e032-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e032-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="2e032-108">[in] Belleği boşaltmak için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2e032-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e032-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e032-109">Requirements</span></span>  
 <span data-ttu-id="2e032-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e032-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e032-111">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2e032-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2e032-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2e032-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2e032-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2e032-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e032-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e032-114">See also</span></span>

- [<span data-ttu-id="2e032-115">StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e032-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="2e032-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e032-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
