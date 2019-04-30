---
title: IMetaDataImport::GetScopeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 17568a46c8e946989af0e401366d7eaa885886da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777578"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="1cf99-102">IMetaDataImport::GetScopeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="1cf99-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="1cf99-103">Geçerli meta veri kapsamdaki ad ve isteğe bağlı olarak derlemesi veya modülü sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="1cf99-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cf99-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cf99-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cf99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cf99-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1cf99-106">[out] Derleme veya modül adı için bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="1cf99-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1cf99-107">[in] Geniş karakter cinsinden boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="1cf99-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1cf99-108">[out] Döndürülen geniş karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="1cf99-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="1cf99-109">[out, isteğe bağlı] Derleme veya Modül sürümü benzersiz olarak tanımlayan bir GUID için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cf99-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cf99-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cf99-110">Remarks</span></span>  
 <span data-ttu-id="1cf99-111">[Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) yöntemi, bu özellikleri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cf99-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cf99-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cf99-112">Requirements</span></span>  
 <span data-ttu-id="1cf99-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cf99-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cf99-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1cf99-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1cf99-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1cf99-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1cf99-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cf99-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf99-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cf99-117">See also</span></span>

- [<span data-ttu-id="1cf99-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cf99-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1cf99-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cf99-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
