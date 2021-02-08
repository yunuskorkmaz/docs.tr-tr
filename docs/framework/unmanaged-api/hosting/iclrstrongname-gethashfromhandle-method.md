---
description: ': ICLRStrongName:: GetHashFromHandle yöntemi hakkında daha fazla bilgi'
title: ICLRStrongName::GetHashFromHandle Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: 30248b5cb5d102adaa06293c92cc4f21e905cba5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799687"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="03710-103">ICLRStrongName::GetHashFromHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="03710-103">ICLRStrongName::GetHashFromHandle Method</span></span>

<span data-ttu-id="03710-104">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="03710-104">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03710-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03710-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03710-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03710-106">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="03710-107">'ndaki Karma hale getirilen dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="03710-107">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="03710-108">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="03710-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="03710-109">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="03710-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="03710-110">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="03710-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="03710-111">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="03710-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="03710-112">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="03710-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03710-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="03710-113">Return Value</span></span>  

 <span data-ttu-id="03710-114">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="03710-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03710-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03710-115">Requirements</span></span>  

 <span data-ttu-id="03710-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03710-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03710-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="03710-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03710-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="03710-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03710-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03710-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03710-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03710-120">See also</span></span>

- [<span data-ttu-id="03710-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03710-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
