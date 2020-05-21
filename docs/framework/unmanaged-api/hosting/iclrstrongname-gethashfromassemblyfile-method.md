---
title: ICLRStrongName::GetHashFromAssemblyFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 007de0365bf70b1f4a9a9e0f01807e7fdac19f54
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762155"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="78c53-102">ICLRStrongName::GetHashFromAssemblyFile Metodu</span><span class="sxs-lookup"><span data-stu-id="78c53-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="78c53-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="78c53-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78c53-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="78c53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78c53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78c53-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="78c53-106">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="78c53-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="78c53-107">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="78c53-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="78c53-108">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="78c53-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="78c53-109">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="78c53-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="78c53-110">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="78c53-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="78c53-111">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="78c53-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78c53-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="78c53-112">Return Value</span></span>  
 <span data-ttu-id="78c53-113">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="78c53-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78c53-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78c53-114">Requirements</span></span>  
 <span data-ttu-id="78c53-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c53-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78c53-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="78c53-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="78c53-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="78c53-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78c53-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78c53-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c53-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78c53-119">See also</span></span>

- [<span data-ttu-id="78c53-120">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78c53-120">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="78c53-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78c53-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
