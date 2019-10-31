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
ms.openlocfilehash: 8db3b1854e334cef4d91d21eb5f666ba2e88fc2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135056"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="1e8d2-102">ICLRStrongName::StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e8d2-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="1e8d2-103">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1e8d2-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e8d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e8d2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e8d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e8d2-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="1e8d2-106">'ndaki Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="1e8d2-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="1e8d2-107">dışı Bayt cinsinden döndürülen arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="1e8d2-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e8d2-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e8d2-108">Return Value</span></span>  
 <span data-ttu-id="1e8d2-109">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="1e8d2-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e8d2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e8d2-110">Requirements</span></span>  
 <span data-ttu-id="1e8d2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e8d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e8d2-112">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1e8d2-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1e8d2-113">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1e8d2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e8d2-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e8d2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8d2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e8d2-115">See also</span></span>

- [<span data-ttu-id="1e8d2-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e8d2-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
