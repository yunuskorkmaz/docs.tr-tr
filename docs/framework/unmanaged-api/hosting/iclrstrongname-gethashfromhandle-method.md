---
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
ms.openlocfilehash: e2d71f7c61b02273bdcaf182f6f79ca3c2a2c75f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762087"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="7b6ee-102">ICLRStrongName::GetHashFromHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="7b6ee-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="7b6ee-103">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b6ee-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7b6ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b6ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b6ee-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="7b6ee-106">'ndaki Karma hale getirilen dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="7b6ee-107">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="7b6ee-108">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="7b6ee-109">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="7b6ee-110">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="7b6ee-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="7b6ee-111">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="7b6ee-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b6ee-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7b6ee-112">Return Value</span></span>  
 <span data-ttu-id="7b6ee-113">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="7b6ee-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b6ee-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b6ee-114">Requirements</span></span>  
 <span data-ttu-id="7b6ee-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b6ee-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b6ee-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7b6ee-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7b6ee-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7b6ee-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b6ee-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b6ee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b6ee-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-119">See also</span></span>

- [<span data-ttu-id="7b6ee-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b6ee-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
