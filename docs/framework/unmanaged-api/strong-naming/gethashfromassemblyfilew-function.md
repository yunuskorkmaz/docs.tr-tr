---
title: GetHashFromAssemblyFileW İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: b895c77850c0457fd2a152c1128c016093599f76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730987"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="a143f-102">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="a143f-102">GetHashFromAssemblyFileW Function</span></span>

<span data-ttu-id="a143f-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="a143f-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="a143f-104">Derleme dosyasının yolu Unicode dize olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a143f-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="a143f-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a143f-105">This function has been deprecated.</span></span> <span data-ttu-id="a143f-106">Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a143f-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a143f-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a143f-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a143f-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a143f-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="a143f-109">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="a143f-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="a143f-110">Bu parametre bir Unicode dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a143f-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a143f-111">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="a143f-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a143f-112">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="a143f-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a143f-113">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="a143f-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a143f-114">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a143f-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a143f-115">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a143f-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a143f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a143f-116">Requirements</span></span>  

 <span data-ttu-id="a143f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a143f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a143f-118">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a143f-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a143f-119">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a143f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a143f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a143f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a143f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a143f-121">See also</span></span>

- [<span data-ttu-id="a143f-122">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a143f-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="a143f-123">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a143f-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="a143f-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a143f-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
