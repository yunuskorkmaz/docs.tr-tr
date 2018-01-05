---
title: "GetHashFromAssemblyFileW İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFileW
helpviewer_keywords: GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 938d7b5633a73aafb81b16fd2fa207160cac4e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="5801f-102">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="5801f-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="5801f-103">Belirtilen karma algoritması kullanılarak belirtilen derleme dosyası karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="5801f-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="5801f-104">Derleme dosyası yolu bir UNICODE dizesi belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5801f-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="5801f-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5801f-105">This function has been deprecated.</span></span> <span data-ttu-id="5801f-106">Kullanım [Iclrstrongname::gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="5801f-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5801f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5801f-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5801f-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5801f-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5801f-109">[in] Karma hale getirilmesi için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="5801f-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="5801f-110">Bu parametre bir UNICODE dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5801f-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5801f-111">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="5801f-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5801f-112">Varsayılan karma algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5801f-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5801f-113">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="5801f-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5801f-114">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5801f-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5801f-115">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5801f-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5801f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5801f-116">Requirements</span></span>  
 <span data-ttu-id="5801f-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5801f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5801f-118">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="5801f-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5801f-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5801f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5801f-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5801f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5801f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5801f-121">See Also</span></span>  
 [<span data-ttu-id="5801f-122">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5801f-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="5801f-123">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5801f-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="5801f-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5801f-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
