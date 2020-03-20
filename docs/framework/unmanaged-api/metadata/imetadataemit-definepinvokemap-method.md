---
title: IMetaDataEmit::DefinePinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: e414bc5a7d537e8d153541f05b22dd91578e8739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177748"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="ac12c-102">IMetaDataEmit::DefinePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac12c-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="ac12c-103">Belirtilen belirteç tarafından başvurulan yöntemin PInvoke imzasının özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ac12c-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac12c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac12c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac12c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac12c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ac12c-106">[içinde] Hedef yönteminin belirteci.</span><span class="sxs-lookup"><span data-stu-id="ac12c-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="ac12c-107">[içinde] Eşleme yapmak için PInvoke tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ac12c-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="ac12c-108">[içinde] Yönetilmeyen bir DLL'de hedef dışa aktarma yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="ac12c-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="ac12c-109">[içinde] Hedef yerel DLL için belirteç.</span><span class="sxs-lookup"><span data-stu-id="ac12c-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac12c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac12c-110">Requirements</span></span>  
 <span data-ttu-id="ac12c-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac12c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac12c-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac12c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac12c-113">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ac12c-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac12c-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac12c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac12c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac12c-115">See also</span></span>

- [<span data-ttu-id="ac12c-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac12c-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ac12c-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac12c-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
