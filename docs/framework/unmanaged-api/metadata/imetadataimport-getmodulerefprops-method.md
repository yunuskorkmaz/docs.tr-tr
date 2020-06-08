---
title: IMetaDataImport::GetModuleRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f1784c9f3085ce188f9e540887dd02064f8448f3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503589"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="f547c-102">IMetaDataImport::GetModuleRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f547c-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="f547c-103">Belirtilen meta veri belirtecinin başvurduğu modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="f547c-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f547c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f547c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f547c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f547c-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="f547c-106">'ndaki Meta veri bilgilerini almak için modüle başvuruda bulunan ModuleRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f547c-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="f547c-107">dışı Modül adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f547c-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f547c-108">'ndaki `szName`Geniş karakter olarak istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="f547c-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f547c-109">dışı `szName`Geniş karakter olarak döndürülen boyutu.</span><span class="sxs-lookup"><span data-stu-id="f547c-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f547c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f547c-110">Requirements</span></span>  
 <span data-ttu-id="f547c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f547c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f547c-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f547c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f547c-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f547c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f547c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f547c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f547c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f547c-115">See also</span></span>

- [<span data-ttu-id="f547c-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f547c-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f547c-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f547c-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
