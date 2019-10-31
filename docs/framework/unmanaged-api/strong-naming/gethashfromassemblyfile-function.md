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
ms.openlocfilehash: 866b34acae333f043d8e13f4d0ebd55f32046334
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140723"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="cda42-102">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="cda42-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="cda42-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="cda42-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="cda42-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="cda42-104">This function has been deprecated.</span></span> <span data-ttu-id="cda42-105">Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cda42-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda42-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cda42-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cda42-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cda42-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="cda42-108">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="cda42-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="cda42-109">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="cda42-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="cda42-110">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="cda42-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="cda42-111">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="cda42-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="cda42-112">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="cda42-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="cda42-113">dışı `pbHash`bayt cinsinden döndürülen boyut.</span><span class="sxs-lookup"><span data-stu-id="cda42-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda42-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cda42-114">Requirements</span></span>  
 <span data-ttu-id="cda42-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda42-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda42-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="cda42-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cda42-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cda42-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cda42-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda42-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda42-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cda42-119">See also</span></span>

- [<span data-ttu-id="cda42-120">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cda42-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="cda42-121">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cda42-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="cda42-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cda42-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
