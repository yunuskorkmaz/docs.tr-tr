---
description: ': IMetaDataImport:: EnumModuleRefs yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumModuleRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: 3e12d3da8ff556cb3add73ade77e11a68bf60223
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688825"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="c7221-103">IMetaDataImport::EnumModuleRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7221-103">IMetaDataImport::EnumModuleRefs Method</span></span>

<span data-ttu-id="c7221-104">İçeri aktarılan modülleri temsil eden ModuleRef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c7221-104">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7221-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7221-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7221-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7221-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c7221-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7221-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c7221-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7221-108">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="c7221-109">dışı ModuleRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="c7221-109">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c7221-110">'ndaki Dizinin en büyük boyutu `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="c7221-110">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="c7221-111">dışı İçinde döndürülen ModuleRef belirteçleri sayısı `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="c7221-111">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7221-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7221-112">Return Value</span></span>  
  
|<span data-ttu-id="c7221-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7221-113">HRESULT</span></span>|<span data-ttu-id="c7221-114">Description</span><span class="sxs-lookup"><span data-stu-id="c7221-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c7221-115">`EnumModuleRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c7221-115">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c7221-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="c7221-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="c7221-117">Bu durumda, `pcModuleRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="c7221-117">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7221-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7221-118">Requirements</span></span>  

 <span data-ttu-id="c7221-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7221-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7221-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7221-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7221-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c7221-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7221-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7221-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7221-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7221-123">See also</span></span>

- [<span data-ttu-id="c7221-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7221-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c7221-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7221-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
