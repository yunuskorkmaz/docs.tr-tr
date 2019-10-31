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
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140703"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="5fe78-102">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="5fe78-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="5fe78-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="5fe78-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="5fe78-104">Derleme dosyasının yolu Unicode dize olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fe78-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="5fe78-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5fe78-105">This function has been deprecated.</span></span> <span data-ttu-id="5fe78-106">Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5fe78-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe78-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fe78-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe78-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fe78-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5fe78-109">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="5fe78-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="5fe78-110">Bu parametre bir Unicode dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fe78-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5fe78-111">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="5fe78-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5fe78-112">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="5fe78-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5fe78-113">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="5fe78-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5fe78-114">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5fe78-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5fe78-115">dışı `pbHash`bayt cinsinden döndürülen boyut.</span><span class="sxs-lookup"><span data-stu-id="5fe78-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe78-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fe78-116">Requirements</span></span>  
 <span data-ttu-id="5fe78-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe78-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe78-118">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="5fe78-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5fe78-119">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5fe78-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5fe78-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe78-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe78-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe78-121">See also</span></span>

- [<span data-ttu-id="5fe78-122">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe78-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="5fe78-123">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe78-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="5fe78-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fe78-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
