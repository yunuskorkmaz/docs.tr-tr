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
ms.openlocfilehash: 8131a9838cc958405ca23c75c702db5ec65a41c8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901190"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="4e156-102">ICLRStrongName::GetHashFromAssemblyFile Metodu</span><span class="sxs-lookup"><span data-stu-id="4e156-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="4e156-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="4e156-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e156-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e156-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e156-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e156-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="4e156-106">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="4e156-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4e156-107">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="4e156-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="4e156-108">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e156-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4e156-109">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="4e156-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4e156-110">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4e156-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4e156-111">dışı `pbHash`bayt cinsinden döndürülen boyut.</span><span class="sxs-lookup"><span data-stu-id="4e156-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e156-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4e156-112">Return Value</span></span>  
 <span data-ttu-id="4e156-113">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="4e156-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e156-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e156-114">Requirements</span></span>  
 <span data-ttu-id="4e156-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e156-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e156-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4e156-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4e156-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4e156-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e156-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e156-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e156-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e156-119">See also</span></span>

- [<span data-ttu-id="4e156-120">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e156-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="4e156-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e156-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
