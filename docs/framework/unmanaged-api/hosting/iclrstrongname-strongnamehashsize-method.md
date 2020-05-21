---
title: ICLRStrongName::StrongNameHashSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
ms.openlocfilehash: 0f4fdcbdfb9db7664920a42b9406a58f9c2de0b8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763117"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="5033a-102">ICLRStrongName::StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5033a-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="5033a-103">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5033a-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5033a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5033a-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5033a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5033a-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="5033a-106">'ndaki Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="5033a-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="5033a-107">dışı Bayt cinsinden döndürülen arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="5033a-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5033a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5033a-108">Return Value</span></span>  
 <span data-ttu-id="5033a-109">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="5033a-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5033a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5033a-110">Requirements</span></span>  
 <span data-ttu-id="5033a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5033a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5033a-112">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="5033a-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5033a-113">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5033a-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5033a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5033a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5033a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5033a-115">See also</span></span>

- [<span data-ttu-id="5033a-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5033a-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
