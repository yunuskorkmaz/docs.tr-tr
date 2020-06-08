---
title: IMetaDataImport::EnumProperties Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 39343ffc88fc9b421b916e33e3e75e4e34fc233d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503798"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="4d120-102">IMetaDataImport::EnumProperties Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d120-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="4d120-103">Belirtilen TypeDef belirtecinin başvurduğu türün özelliklerini temsil eden PropertyDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="4d120-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d120-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4d120-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d120-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d120-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4d120-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4d120-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4d120-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d120-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="4d120-108">'ndaki Numaralandırılacak özellikleri olan türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="4d120-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="4d120-109">dışı PropertyDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="4d120-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4d120-110">'ndaki Dizinin en büyük boyutu `rProperties` .</span><span class="sxs-lookup"><span data-stu-id="4d120-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="4d120-111">dışı İçinde döndürülen PropertyDef belirteçleri sayısı `rProperties` .</span><span class="sxs-lookup"><span data-stu-id="4d120-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d120-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d120-112">Return Value</span></span>  
  
|<span data-ttu-id="4d120-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d120-113">HRESULT</span></span>|<span data-ttu-id="4d120-114">Description</span><span class="sxs-lookup"><span data-stu-id="4d120-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4d120-115">`EnumProperties`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4d120-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4d120-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="4d120-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="4d120-117">Bu durumda, `pcProperties` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="4d120-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d120-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d120-118">Requirements</span></span>  
 <span data-ttu-id="4d120-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d120-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d120-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4d120-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d120-121">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4d120-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d120-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d120-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d120-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d120-123">See also</span></span>

- [<span data-ttu-id="4d120-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d120-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4d120-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d120-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
