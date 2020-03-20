---
title: GetHashFromFile İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176987"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="9b797-102">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="9b797-102">GetHashFromFile Function</span></span>
<span data-ttu-id="9b797-103">Belirtilen dosyanın içeriği üzerinde karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b797-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="9b797-104">Bu işlev amortismana kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="9b797-104">This function has been deprecated.</span></span> <span data-ttu-id="9b797-105">Bunun yerine [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9b797-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b797-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b797-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b797-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b797-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="9b797-108">[içinde] Karma dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="9b797-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9b797-109">[içinde, dışarı] Karma oluştururken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="9b797-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="9b797-110">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlanan algoritmalardır.</span><span class="sxs-lookup"><span data-stu-id="9b797-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="9b797-111">0 `piHashAlg` olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9b797-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9b797-112">[çıkış] Oluşturulan karma içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="9b797-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9b797-113">[içinde] Tamponun işaret eden `pbHash` maksimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="9b797-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9b797-114">[çıkış] Döndürülen baytların `pbHash`boyutu.</span><span class="sxs-lookup"><span data-stu-id="9b797-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b797-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b797-115">Remarks</span></span>  
 <span data-ttu-id="9b797-116">Bu işlev [GetHashFromFileW](gethashfromfilew-function.md)ile aynıdır, ancak dosya adı belirtimi Unicode yerine ANSI'dir.</span><span class="sxs-lookup"><span data-stu-id="9b797-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b797-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b797-117">Requirements</span></span>  
 <span data-ttu-id="9b797-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b797-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b797-119">**Üstbilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9b797-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9b797-120">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="9b797-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b797-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b797-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b797-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b797-122">See also</span></span>

- [<span data-ttu-id="9b797-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b797-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="9b797-124">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b797-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="9b797-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b797-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
