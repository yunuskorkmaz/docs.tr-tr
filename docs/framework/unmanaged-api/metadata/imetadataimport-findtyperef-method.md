---
description: ': IMetaDataImport:: FindTypeRef metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 11e966256b5e75c1acff0bf1e6de0c96dc03e6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745573"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="ec58c-103">IMetaDataImport::FindTypeRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec58c-103">IMetaDataImport::FindTypeRef Method</span></span>

<span data-ttu-id="ec58c-104"><xref:System.Type>Belirtilen kapsamda olan ve belirtilen ada sahip olan başvurunun TypeRef belirtecine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ec58c-104">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec58c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec58c-105">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec58c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec58c-106">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="ec58c-107">'ndaki Sırasıyla tür başvurusunun tanımlandığı modül, derleme veya türü belirten bir ModuleRef, AssemblyRef veya TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="ec58c-107">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="ec58c-108">'ndaki Arama yapılacak tür başvurusunun adı.</span><span class="sxs-lookup"><span data-stu-id="ec58c-108">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="ec58c-109">dışı Eşleşen TypeRef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec58c-109">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec58c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec58c-110">Requirements</span></span>  

 <span data-ttu-id="ec58c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec58c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec58c-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec58c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec58c-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ec58c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec58c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec58c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec58c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec58c-115">See also</span></span>

- [<span data-ttu-id="ec58c-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec58c-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ec58c-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec58c-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
