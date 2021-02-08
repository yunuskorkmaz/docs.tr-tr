---
description: ': ICLRStrongName:: StrongNameHashSize yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 74781f0eaec720a84a242e6a9637036408652601
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799596"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="3e03e-103">ICLRStrongName::StrongNameHashSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e03e-103">ICLRStrongName::StrongNameHashSize Method</span></span>

<span data-ttu-id="3e03e-104">Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="3e03e-104">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e03e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e03e-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e03e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e03e-106">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="3e03e-107">'ndaki Arabellek boyutunu hesaplamak için kullanılan karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="3e03e-107">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="3e03e-108">dışı Bayt cinsinden döndürülen arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="3e03e-108">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e03e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3e03e-109">Return Value</span></span>  

 <span data-ttu-id="3e03e-110">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="3e03e-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e03e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e03e-111">Requirements</span></span>  

 <span data-ttu-id="3e03e-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e03e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e03e-113">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3e03e-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3e03e-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3e03e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e03e-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e03e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e03e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e03e-116">See also</span></span>

- [<span data-ttu-id="3e03e-117">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e03e-117">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
