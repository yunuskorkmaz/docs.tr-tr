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
ms.openlocfilehash: ec32b285713e3e506359c4c831eb076d2b47a967
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499790"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="dbfef-102">IMetaDataImport::GetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dbfef-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="dbfef-103">Bir ModuleRef PInvoke çağrısına hedef derleme temsil etmek için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="dbfef-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbfef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbfef-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dbfef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbfef-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="dbfef-106">[in] PInvoke eşleme meta verilerini almak için fieldDef simgesi veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="dbfef-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="dbfef-107">[out] Eşleme için kullanılan bayraklar işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dbfef-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="dbfef-108">Gelen bir bit maskesi değerdir [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="dbfef-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="dbfef-109">[out] Yönetilmeyen DLL hedef adı.</span><span class="sxs-lookup"><span data-stu-id="dbfef-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="dbfef-110">[in] Geniş karakter cinsinden boyutu `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="dbfef-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="dbfef-111">[out] Döndürülen geniş karakter sayısını `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="dbfef-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="dbfef-112">[out] Yönetilmeyen hedef nesne kitaplığı temsil eden bir ModuleRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dbfef-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbfef-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbfef-113">Requirements</span></span>  
 <span data-ttu-id="dbfef-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbfef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbfef-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="dbfef-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbfef-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dbfef-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dbfef-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbfef-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbfef-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbfef-118">See also</span></span>
- [<span data-ttu-id="dbfef-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbfef-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dbfef-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbfef-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
