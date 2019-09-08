---
title: GetHashFromAssemblyFile İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f984d44d0a8acb85562a58653dfd2882053a0ce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799279"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="15eb5-102">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="15eb5-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="15eb5-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="15eb5-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="15eb5-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="15eb5-104">This function has been deprecated.</span></span> <span data-ttu-id="15eb5-105">Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="15eb5-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15eb5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15eb5-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15eb5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15eb5-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="15eb5-108">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="15eb5-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="15eb5-109">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="15eb5-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="15eb5-110">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="15eb5-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="15eb5-111">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="15eb5-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="15eb5-112">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="15eb5-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="15eb5-113">dışı Bayt cinsinden döndürülen boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="15eb5-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15eb5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15eb5-114">Requirements</span></span>  
 <span data-ttu-id="15eb5-115">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15eb5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15eb5-116">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="15eb5-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="15eb5-117">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="15eb5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15eb5-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15eb5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15eb5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15eb5-119">See also</span></span>

- [<span data-ttu-id="15eb5-120">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15eb5-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="15eb5-121">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15eb5-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="15eb5-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15eb5-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
