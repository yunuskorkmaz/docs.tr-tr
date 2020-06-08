---
title: IMetaDataImport::EnumFields Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 1ff2dd64dc4797bc485550c30f7204644a3adb47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492284"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="79c84-102">IMetaDataImport::EnumFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79c84-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="79c84-103">Belirtilen TypeDef belirtecinin başvurduğu tür için FieldDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="79c84-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c84-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="79c84-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79c84-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79c84-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="79c84-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79c84-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="79c84-107">'ndaki Alanları Numaralandırılacak olan sınıfın TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="79c84-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="79c84-108">dışı FieldDef belirteçlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="79c84-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="79c84-109">'ndaki Dizinin en büyük boyutu `rFields` .</span><span class="sxs-lookup"><span data-stu-id="79c84-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="79c84-110">dışı İçinde döndürülen FieldDef belirteçlerinin gerçek sayısı `rFields` .</span><span class="sxs-lookup"><span data-stu-id="79c84-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79c84-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="79c84-111">Return Value</span></span>  
  
|<span data-ttu-id="79c84-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79c84-112">HRESULT</span></span>|<span data-ttu-id="79c84-113">Description</span><span class="sxs-lookup"><span data-stu-id="79c84-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="79c84-114">`EnumFields`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="79c84-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="79c84-115">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="79c84-115">There are no fields to enumerate.</span></span> <span data-ttu-id="79c84-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="79c84-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79c84-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79c84-117">Requirements</span></span>  
 <span data-ttu-id="79c84-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79c84-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c84-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="79c84-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79c84-120">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="79c84-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79c84-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79c84-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c84-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79c84-122">See also</span></span>

- [<span data-ttu-id="79c84-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79c84-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="79c84-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79c84-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
