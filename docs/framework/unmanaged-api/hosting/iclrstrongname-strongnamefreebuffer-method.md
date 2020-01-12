---
title: ICLRStrongName::StrongNameFreeBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 9aeac02e865214db8fec25621f1bf204a93b36f6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901133"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="5d8da-102">ICLRStrongName::StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d8da-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="5d8da-103">[ICLRStrongName:: StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md):: StrongNameTokenFromPublicKey veya [ICLRStrongName:: StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)gibi tanımlayıcı bir ad yöntemine önceki bir çağrı ile ayrılmış belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="5d8da-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d8da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d8da-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d8da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d8da-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="5d8da-106">'ndaki Boşaltılacak belleğin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5d8da-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d8da-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d8da-107">Return Value</span></span>  
 <span data-ttu-id="5d8da-108">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="5d8da-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d8da-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d8da-109">Requirements</span></span>  
 <span data-ttu-id="5d8da-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d8da-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d8da-111">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="5d8da-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5d8da-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5d8da-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d8da-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d8da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d8da-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8da-114">See also</span></span>

- [<span data-ttu-id="5d8da-115">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d8da-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
