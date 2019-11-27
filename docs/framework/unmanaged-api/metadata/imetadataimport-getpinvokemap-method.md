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
ms.openlocfilehash: c458fef77b49f522ca21dd5487731f4d43588cea
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437104"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="e82bb-102">IMetaDataImport::GetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e82bb-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="e82bb-103">Bir PInvoke çağrısının hedef derlemesini temsil eden bir ModuleRef belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="e82bb-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e82bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e82bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e82bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e82bb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e82bb-106">'ndaki İçin PInvoke eşleme meta verilerini almak için FieldDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="e82bb-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="e82bb-107">dışı Eşleme için kullanılan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e82bb-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="e82bb-108">Bu değer, [Corpınvokemap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) numaralandırmasındaki bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="e82bb-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="e82bb-109">dışı Yönetilmeyen hedef DLL 'in adı.</span><span class="sxs-lookup"><span data-stu-id="e82bb-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="e82bb-110">'ndaki `szImportName`geniş karakterdeki boyut.</span><span class="sxs-lookup"><span data-stu-id="e82bb-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="e82bb-111">dışı `szImportName`' de döndürülen geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="e82bb-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="e82bb-112">dışı Yönetilmeyen hedef nesne kitaplığını temsil eden bir ModuleRef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e82bb-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e82bb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e82bb-113">Requirements</span></span>  
 <span data-ttu-id="e82bb-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e82bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e82bb-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e82bb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e82bb-116">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e82bb-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e82bb-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e82bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82bb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e82bb-118">See also</span></span>

- [<span data-ttu-id="e82bb-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e82bb-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e82bb-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e82bb-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
