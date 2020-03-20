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
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177209"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="9cb0b-102">IMetaDataImport::GetRVA Metodu</span><span class="sxs-lookup"><span data-stu-id="9cb0b-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="9cb0b-103">Belirtilen belirteç tarafından temsil edilen yöntem veya alanın göreli sanal adresi (RVA) ve uygulama bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cb0b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9cb0b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9cb0b-106">[içinde] RVA'yı döndürecek kod nesnesini temsil eden bir MethodDef veya FieldDef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="9cb0b-107">Belirteç bir FieldDef ise, alan küresel bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="9cb0b-108">[çıkış] Belirteç tarafından temsil edilen kod nesnesinin göreli sanal adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="9cb0b-109">[çıkış] Yöntem için uygulama bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="9cb0b-110">Bu değer [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) numaralandırma bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="9cb0b-111">Değeri `pdwImplFlags` yalnızca Bir MethodDef belirteci ise `tk` geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb0b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9cb0b-112">Requirements</span></span>  
 <span data-ttu-id="9cb0b-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cb0b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb0b-114">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9cb0b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9cb0b-115">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="9cb0b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9cb0b-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb0b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb0b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cb0b-117">See also</span></span>

- [<span data-ttu-id="9cb0b-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9cb0b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9cb0b-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9cb0b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
