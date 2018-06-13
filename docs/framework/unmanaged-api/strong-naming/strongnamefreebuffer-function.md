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
ms.openlocfilehash: 1a129608370cd72967e0c441eff12b4aca7e638c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455094"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="7eeb6-102">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eeb6-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="7eeb6-103">Önceki bir güçlü ad işlevi çağrısı ile ayrıldı bellek boşaltır [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), veya [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="7eeb6-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="7eeb6-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="7eeb6-104">This function has been deprecated.</span></span> <span data-ttu-id="7eeb6-105">Kullanım [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="7eeb6-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eeb6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7eeb6-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eeb6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7eeb6-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="7eeb6-108">[in] Bellek boşaltmak için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7eeb6-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eeb6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7eeb6-109">Requirements</span></span>  
 <span data-ttu-id="7eeb6-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eeb6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eeb6-111">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="7eeb6-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7eeb6-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7eeb6-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7eeb6-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eeb6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eeb6-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7eeb6-114">See Also</span></span>  
 [<span data-ttu-id="7eeb6-115">StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7eeb6-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="7eeb6-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7eeb6-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
