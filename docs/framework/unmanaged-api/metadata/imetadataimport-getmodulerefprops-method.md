---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataImport:: GetModuleRefProps yöntemi'
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
ms.openlocfilehash: 3e6b212ddad5eefb06942c3fd4b89411b277f761
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753360"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="3fc45-103">IMetaDataImport::GetModuleRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fc45-103">IMetaDataImport::GetModuleRefProps Method</span></span>

<span data-ttu-id="3fc45-104">Belirtilen meta veri belirtecinin başvurduğu modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="3fc45-104">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc45-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fc45-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc45-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fc45-106">Parameters</span></span>  

 `mur`  
 <span data-ttu-id="3fc45-107">'ndaki Meta veri bilgilerini almak için modüle başvuruda bulunan ModuleRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3fc45-107">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="3fc45-108">dışı Modül adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="3fc45-108">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3fc45-109">'ndaki `szName` Geniş karakter olarak istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="3fc45-109">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="3fc45-110">dışı `szName` Geniş karakter olarak döndürülen boyutu.</span><span class="sxs-lookup"><span data-stu-id="3fc45-110">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc45-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fc45-111">Requirements</span></span>  

 <span data-ttu-id="3fc45-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fc45-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc45-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3fc45-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fc45-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3fc45-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fc45-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc45-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc45-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fc45-116">See also</span></span>

- [<span data-ttu-id="3fc45-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fc45-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3fc45-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fc45-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
