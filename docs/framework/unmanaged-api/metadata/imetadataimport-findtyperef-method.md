---
title: IMetaDataImport::FindTypeRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 545fe1e1d9e641d2225ad92c11453558dc4b97d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491504"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="8a7d8-102">IMetaDataImport::FindTypeRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a7d8-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="8a7d8-103"><xref:System.Type>Belirtilen kapsamda olan ve belirtilen ada sahip olan başvurunun TypeRef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a7d8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8a7d8-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a7d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a7d8-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="8a7d8-106">'ndaki Sırasıyla tür başvurusunun tanımlandığı modül, derleme veya türü belirten bir ModuleRef, AssemblyRef veya TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a7d8-107">'ndaki Arama yapılacak tür başvurusunun adı.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="8a7d8-108">dışı Eşleşen TypeRef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a7d8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a7d8-109">Requirements</span></span>  
 <span data-ttu-id="8a7d8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a7d8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a7d8-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a7d8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a7d8-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8a7d8-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a7d8-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a7d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7d8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-114">See also</span></span>

- [<span data-ttu-id="8a7d8-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a7d8-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8a7d8-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a7d8-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
