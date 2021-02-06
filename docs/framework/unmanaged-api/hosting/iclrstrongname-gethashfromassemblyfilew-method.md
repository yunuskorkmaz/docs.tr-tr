---
description: ': ICLRStrongName:: GetHashFromAssemblyFileW yöntemi hakkında daha fazla bilgi'
title: ICLRStrongName::GetHashFromAssemblyFileW Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 27123ed8217d49765fe3fd7c19efc92f4e770722
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637085"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="9263f-103">ICLRStrongName::GetHashFromAssemblyFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="9263f-103">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>

<span data-ttu-id="9263f-104">Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9263f-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9263f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9263f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9263f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9263f-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="9263f-107">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="9263f-107">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="9263f-108">Bu parametre bir Unicode dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9263f-108">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9263f-109">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="9263f-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9263f-110">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="9263f-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9263f-111">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="9263f-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9263f-112">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="9263f-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9263f-113">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="9263f-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9263f-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9263f-114">Return Value</span></span>  

 <span data-ttu-id="9263f-115">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="9263f-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9263f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9263f-116">Requirements</span></span>  

 <span data-ttu-id="9263f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9263f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9263f-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9263f-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9263f-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9263f-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9263f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9263f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9263f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9263f-121">See also</span></span>

- [<span data-ttu-id="9263f-122">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9263f-122">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="9263f-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9263f-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
