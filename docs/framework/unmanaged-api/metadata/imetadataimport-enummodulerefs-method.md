---
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
ms.openlocfilehash: fe7350e6d8e400ae37b5b8b7854a56f3c5c53ea7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491767"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="9a776-102">IMetaDataImport::EnumModuleRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a776-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="9a776-103">İçeri aktarılan modülleri temsil eden ModuleRef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="9a776-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a776-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9a776-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a776-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a776-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9a776-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a776-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9a776-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a776-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="9a776-108">dışı ModuleRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="9a776-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9a776-109">'ndaki Dizinin en büyük boyutu `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="9a776-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="9a776-110">dışı İçinde döndürülen ModuleRef belirteçleri sayısı `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="9a776-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a776-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a776-111">Return Value</span></span>  
  
|<span data-ttu-id="9a776-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a776-112">HRESULT</span></span>|<span data-ttu-id="9a776-113">Description</span><span class="sxs-lookup"><span data-stu-id="9a776-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9a776-114">`EnumModuleRefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9a776-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9a776-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="9a776-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="9a776-116">Bu durumda, `pcModuleRefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="9a776-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a776-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a776-117">Requirements</span></span>  
 <span data-ttu-id="9a776-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a776-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a776-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9a776-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a776-120">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9a776-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a776-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a776-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a776-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a776-122">See also</span></span>

- [<span data-ttu-id="9a776-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a776-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9a776-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a776-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
