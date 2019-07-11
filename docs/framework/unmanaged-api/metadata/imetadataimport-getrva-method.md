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
ms.openlocfilehash: d305aa59c1b9e9e1225b30f12e36fc689d584db1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778890"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="98988-102">IMetaDataImport::GetRVA Metodu</span><span class="sxs-lookup"><span data-stu-id="98988-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="98988-103">Göreli sanal adres (RVA) ve yöntem veya belirtilen belirteci tarafından temsil edilen alan uygulama bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="98988-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98988-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98988-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98988-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98988-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="98988-106">[in] İçin RVA döndürmek için kod nesneyi temsil eden bir MethodDef veya fieldDef simgesi meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="98988-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="98988-107">Bir fieldDef simgesi belirteci ise alan genel bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98988-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="98988-108">[out] Göreli sanal adres belirteci tarafından temsil edilen kod nesnenin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98988-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="98988-109">[out] Uygulama bayrakları yöntemi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98988-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="98988-110">Gelen bir bit maskesi değerdir [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="98988-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="98988-111">Değerini `pdwImplFlags` geçerli yalnızca `tk` MethodDef belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="98988-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98988-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98988-112">Requirements</span></span>  
 <span data-ttu-id="98988-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98988-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98988-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="98988-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98988-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="98988-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98988-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98988-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98988-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98988-117">See also</span></span>

- [<span data-ttu-id="98988-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98988-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="98988-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98988-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
