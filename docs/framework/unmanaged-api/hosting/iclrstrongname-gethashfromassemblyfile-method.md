---
description: ': ICLRStrongName:: GetHashFromAssemblyFile Yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 40a8e2aabe9ade00243c535d63389f4265cc6ab0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799711"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="14243-103">ICLRStrongName::GetHashFromAssemblyFile Metodu</span><span class="sxs-lookup"><span data-stu-id="14243-103">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>

<span data-ttu-id="14243-104">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="14243-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14243-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14243-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14243-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14243-106">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="14243-107">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="14243-107">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="14243-108">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="14243-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="14243-109">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="14243-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="14243-110">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="14243-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="14243-111">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="14243-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="14243-112">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="14243-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14243-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="14243-113">Return Value</span></span>  

 <span data-ttu-id="14243-114">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="14243-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14243-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14243-115">Requirements</span></span>  

 <span data-ttu-id="14243-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14243-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14243-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="14243-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="14243-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="14243-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14243-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14243-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14243-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14243-120">See also</span></span>

- [<span data-ttu-id="14243-121">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14243-121">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="14243-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14243-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
