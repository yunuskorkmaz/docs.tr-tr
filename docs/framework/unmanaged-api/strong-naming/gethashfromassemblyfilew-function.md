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
ms.openlocfilehash: 832d66eee14680870e70f1e0e8d40987eff3257f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457580"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="10217-102">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="10217-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="10217-103">Belirtilen karma algoritması kullanılarak belirtilen derleme dosyası karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="10217-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="10217-104">Derleme dosyası yolu bir UNICODE dizesi belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="10217-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="10217-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="10217-105">This function has been deprecated.</span></span> <span data-ttu-id="10217-106">Kullanım [Iclrstrongname::gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="10217-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10217-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10217-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10217-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10217-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="10217-109">[in] Karma hale getirilmesi için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="10217-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="10217-110">Bu parametre bir UNICODE dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10217-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="10217-111">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="10217-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="10217-112">Varsayılan karma algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="10217-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="10217-113">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="10217-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="10217-114">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="10217-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="10217-115">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="10217-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10217-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10217-116">Requirements</span></span>  
 <span data-ttu-id="10217-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10217-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10217-118">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="10217-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="10217-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="10217-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10217-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10217-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10217-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10217-121">See Also</span></span>  
 [<span data-ttu-id="10217-122">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10217-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="10217-123">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10217-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="10217-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10217-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
