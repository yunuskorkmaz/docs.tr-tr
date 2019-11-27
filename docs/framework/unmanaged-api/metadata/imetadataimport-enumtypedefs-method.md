---
title: IMetaDataImport::EnumTypeDefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450000"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="21566-102">IMetaDataImport::EnumTypeDefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21566-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="21566-103">Geçerli kapsam içindeki tüm türleri temsil eden TypeDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="21566-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21566-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21566-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21566-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21566-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="21566-106">dışı Yeni Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21566-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="21566-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21566-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="21566-108">'ndaki TypeDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="21566-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="21566-109">'ndaki `rTypeDefs` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="21566-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="21566-110">dışı `rTypeDefs`' de döndürülen TypeDef belirteçleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="21566-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21566-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21566-111">Return Value</span></span>  
  
|<span data-ttu-id="21566-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21566-112">HRESULT</span></span>|<span data-ttu-id="21566-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21566-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="21566-114">`EnumTypeDefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="21566-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="21566-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="21566-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="21566-116">Bu durumda `pcTypeDefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="21566-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21566-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21566-117">Remarks</span></span>  
 <span data-ttu-id="21566-118">TypeDef belirteci, bir sınıf veya arabirim gibi bir türü ve bir genişletilebilirlik mekanizması aracılığıyla eklenen herhangi bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21566-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21566-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21566-119">Requirements</span></span>  
 <span data-ttu-id="21566-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21566-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21566-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="21566-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21566-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="21566-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21566-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21566-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21566-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21566-124">See also</span></span>

- [<span data-ttu-id="21566-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21566-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="21566-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21566-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
