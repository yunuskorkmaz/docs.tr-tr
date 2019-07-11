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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d034f15db8f3d452a055c127bb7095667c089ffe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772055"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="37ca7-102">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="37ca7-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="37ca7-103">Belirtilen karma algoritması kullanılarak, belirtilen derleme dosyasının bir karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="37ca7-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="37ca7-104">Derleme dosyası yolu bir Unicode dize olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="37ca7-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="37ca7-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="37ca7-105">This function has been deprecated.</span></span> <span data-ttu-id="37ca7-106">Kullanım [Iclrstrongname::gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="37ca7-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ca7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37ca7-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37ca7-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37ca7-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="37ca7-109">[in] Karma hale getirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="37ca7-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="37ca7-110">Bu parametre, bir Unicode dize olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="37ca7-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="37ca7-111">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="37ca7-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="37ca7-112">Sıfır varsayılan karma algoritması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="37ca7-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="37ca7-113">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="37ca7-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="37ca7-114">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="37ca7-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="37ca7-115">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="37ca7-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ca7-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37ca7-116">Requirements</span></span>  
 <span data-ttu-id="37ca7-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ca7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ca7-118">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="37ca7-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="37ca7-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="37ca7-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37ca7-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37ca7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ca7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37ca7-121">See also</span></span>

- [<span data-ttu-id="37ca7-122">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37ca7-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="37ca7-123">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37ca7-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="37ca7-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37ca7-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
