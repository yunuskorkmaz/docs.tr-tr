---
title: IMetaDataImport::GetPinvokeMap Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a28d628040a35d309515703563239a5f802dc4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="cea86-102">IMetaDataImport::GetPinvokeMap Metodu</span><span class="sxs-lookup"><span data-stu-id="cea86-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="cea86-103">Bir ModuleRef PInvoke çağrısı hedef derlemenin temsil etmek için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="cea86-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cea86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cea86-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cea86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cea86-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="cea86-106">[in] PInvoke eşleme meta verilerini almak için fieldDef simgesi veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="cea86-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="cea86-107">[out] Eşleme için kullanılan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cea86-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="cea86-108">Bu değer gelen bir bit maskesi olan [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="cea86-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="cea86-109">[out] Yönetilmeyen DLL hedef adı.</span><span class="sxs-lookup"><span data-stu-id="cea86-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="cea86-110">[in] Geniş karakter cinsinden boyutu `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="cea86-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="cea86-111">[out] Döndürülen geniş karakter sayısını `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="cea86-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="cea86-112">[out] Yönetilmeyen hedef nesne kitaplığı temsil eden bir ModuleRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cea86-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cea86-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cea86-113">Requirements</span></span>  
 <span data-ttu-id="cea86-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cea86-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cea86-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cea86-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cea86-116">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cea86-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cea86-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cea86-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea86-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cea86-118">See Also</span></span>  
 [<span data-ttu-id="cea86-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cea86-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cea86-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cea86-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
