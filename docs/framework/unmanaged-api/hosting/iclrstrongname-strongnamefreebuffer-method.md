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
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504010"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="50a13-102">ICLRStrongName::StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50a13-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="50a13-103">[ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName](iclrstrongname-strongnametokenfrompublickey-method.md):: StrongNameTokenFromPublicKey veya [ICLRStrongName:: StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)gibi tanımlayıcı bir ad yöntemine önceki bir çağrı ile ayrılmış belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="50a13-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a13-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="50a13-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50a13-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="50a13-106">'ndaki Boşaltılacak belleğin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50a13-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50a13-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50a13-107">Return Value</span></span>  
 <span data-ttu-id="50a13-108">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="50a13-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a13-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50a13-109">Requirements</span></span>  
 <span data-ttu-id="50a13-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50a13-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a13-111">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="50a13-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="50a13-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="50a13-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50a13-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50a13-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a13-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50a13-114">See also</span></span>

- [<span data-ttu-id="50a13-115">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50a13-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
