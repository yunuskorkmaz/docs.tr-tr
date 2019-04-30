---
title: IMetaDataImport::GetPinvokeMap Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99aea385cf5e3c8bcf7cf39b7cc5618f99f8a631
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777591"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="1e0b7-102">IMetaDataImport::GetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e0b7-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="1e0b7-103">Bir ModuleRef PInvoke çağrısına hedef derleme temsil etmek için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e0b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e0b7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1e0b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e0b7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1e0b7-106">[in] PInvoke eşleme meta verilerini almak için fieldDef simgesi veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="1e0b7-107">[out] Eşleme için kullanılan bayraklar işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="1e0b7-108">Gelen bir bit maskesi değerdir [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="1e0b7-109">[out] Yönetilmeyen DLL hedef adı.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="1e0b7-110">[in] Geniş karakter cinsinden boyutu `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="1e0b7-111">[out] Döndürülen geniş karakter sayısını `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="1e0b7-112">[out] Yönetilmeyen hedef nesne kitaplığı temsil eden bir ModuleRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e0b7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e0b7-113">Requirements</span></span>  
 <span data-ttu-id="1e0b7-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e0b7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e0b7-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1e0b7-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e0b7-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1e0b7-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e0b7-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e0b7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e0b7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-118">See also</span></span>

- [<span data-ttu-id="1e0b7-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e0b7-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1e0b7-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e0b7-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
