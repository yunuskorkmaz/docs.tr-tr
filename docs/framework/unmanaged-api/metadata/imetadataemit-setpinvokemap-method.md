---
title: IMetaDataEmit::SetPinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 4c68754bc44fe035fd8e7143c52895928beae395
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175596"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="1e2f4-102">IMetaDataEmit::SetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e2f4-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="1e2f4-103">Bir yöntemin PInvoke imzasının özelliklerini ayarlar veya değiştirir, [iMetaDataEmit::DefinePinvokeMap.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)</span><span class="sxs-lookup"><span data-stu-id="1e2f4-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e2f4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e2f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e2f4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1e2f4-106">[içinde] Haritalama bilgilerinin `mdToken` uygulandığı yer.</span><span class="sxs-lookup"><span data-stu-id="1e2f4-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="1e2f4-107">[içinde] Eşleme yapmak için PInvoke tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="1e2f4-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="1e2f4-108">Bu `CorPinvokeMap` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="1e2f4-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="1e2f4-109">[içinde] Yerel DLL'deki hedef dışa aktarmanın adı.</span><span class="sxs-lookup"><span data-stu-id="1e2f4-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="1e2f4-110">[içinde] Hedef `mdModuleRef` in belirteç leri yönetilmemiş DLL.</span><span class="sxs-lookup"><span data-stu-id="1e2f4-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e2f4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e2f4-111">Requirements</span></span>  
 <span data-ttu-id="1e2f4-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e2f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e2f4-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1e2f4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e2f4-114">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1e2f4-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e2f4-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e2f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2f4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e2f4-116">See also</span></span>

- [<span data-ttu-id="1e2f4-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e2f4-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1e2f4-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e2f4-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
