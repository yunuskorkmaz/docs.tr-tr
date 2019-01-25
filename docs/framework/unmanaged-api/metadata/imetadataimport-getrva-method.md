---
title: IMetaDataImport::GetRVA Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 126cc9d407e2653fdb3f4ea7b03fa05c24a572d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629135"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="0d5d6-102">IMetaDataImport::GetRVA Metodu</span><span class="sxs-lookup"><span data-stu-id="0d5d6-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="0d5d6-103">Göreli sanal adres (RVA) ve yöntem veya belirtilen belirteci tarafından temsil edilen alan uygulama bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d5d6-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d5d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d5d6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0d5d6-106">[in] İçin RVA döndürmek için kod nesneyi temsil eden bir MethodDef veya fieldDef simgesi meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="0d5d6-107">Bir fieldDef simgesi belirteci ise alan genel bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="0d5d6-108">[out] Göreli sanal adres belirteci tarafından temsil edilen kod nesnenin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="0d5d6-109">[out] Uygulama bayrakları yöntemi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="0d5d6-110">Gelen bir bit maskesi değerdir [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="0d5d6-111">Değerini `pdwImplFlags` geçerli yalnızca `tk` MethodDef belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d5d6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d5d6-112">Requirements</span></span>  
 <span data-ttu-id="0d5d6-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d5d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d5d6-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0d5d6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d5d6-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0d5d6-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d5d6-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d5d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5d6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-117">See also</span></span>
- [<span data-ttu-id="0d5d6-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d5d6-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0d5d6-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d5d6-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
