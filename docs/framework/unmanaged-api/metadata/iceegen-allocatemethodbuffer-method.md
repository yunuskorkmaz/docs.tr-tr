---
title: ICeeGen::AllocateMethodBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 080c16d3a7baceaa277b3418ac2e17391090f00c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750600"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="65ad6-102">ICeeGen::AllocateMethodBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65ad6-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="65ad6-103">Bir yöntem için belirtilen boyutta bir arabellek oluşturur ve yöntemin göreli sanal adres alır.</span><span class="sxs-lookup"><span data-stu-id="65ad6-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="65ad6-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="65ad6-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ad6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65ad6-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ad6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65ad6-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="65ad6-107">[in] Oluşturmak için arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="65ad6-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="65ad6-108">[out] Döndürülen arabelleği.</span><span class="sxs-lookup"><span data-stu-id="65ad6-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="65ad6-109">[out] Yöntemin göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="65ad6-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ad6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65ad6-110">Requirements</span></span>  
 <span data-ttu-id="65ad6-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ad6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ad6-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="65ad6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65ad6-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="65ad6-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65ad6-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ad6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ad6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65ad6-115">See also</span></span>

- [<span data-ttu-id="65ad6-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65ad6-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
