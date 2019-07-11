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
ms.openlocfilehash: 026115adc01e7dcdac3012255f0378cff6348f89
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780696"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="24bab-102">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="24bab-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="24bab-103">Belirtilen karma algoritması kullanılarak, belirtilen derleme dosyasının bir karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="24bab-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="24bab-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="24bab-104">This function has been deprecated.</span></span> <span data-ttu-id="24bab-105">Kullanım [Iclrstrongname::gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="24bab-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24bab-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24bab-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24bab-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24bab-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="24bab-108">[in] Karma hale getirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="24bab-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="24bab-109">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="24bab-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="24bab-110">Sıfır varsayılan karma algoritması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="24bab-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="24bab-111">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="24bab-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="24bab-112">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="24bab-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="24bab-113">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="24bab-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24bab-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24bab-114">Requirements</span></span>  
 <span data-ttu-id="24bab-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24bab-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24bab-116">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="24bab-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="24bab-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="24bab-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24bab-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24bab-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24bab-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24bab-119">See also</span></span>

- [<span data-ttu-id="24bab-120">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24bab-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="24bab-121">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24bab-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="24bab-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24bab-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
