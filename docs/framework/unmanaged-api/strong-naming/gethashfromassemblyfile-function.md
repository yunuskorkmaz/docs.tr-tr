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
ms.openlocfilehash: caefc9773b0d208f8b20847b664f7bc017d2c076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731000"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="bc0fc-102">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="bc0fc-102">GetHashFromAssemblyFile Function</span></span>

<span data-ttu-id="bc0fc-103">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="bc0fc-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-104">This function has been deprecated.</span></span> <span data-ttu-id="bc0fc-105">Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0fc-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bc0fc-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc0fc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc0fc-107">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="bc0fc-108">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="bc0fc-109">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="bc0fc-110">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="bc0fc-111">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="bc0fc-112">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="bc0fc-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="bc0fc-113">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="bc0fc-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0fc-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc0fc-114">Requirements</span></span>  

 <span data-ttu-id="bc0fc-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc0fc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc0fc-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bc0fc-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bc0fc-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bc0fc-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc0fc-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0fc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0fc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc0fc-119">See also</span></span>

- [<span data-ttu-id="bc0fc-120">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc0fc-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="bc0fc-121">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc0fc-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="bc0fc-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc0fc-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
