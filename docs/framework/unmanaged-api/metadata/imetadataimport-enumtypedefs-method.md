---
description: ': IMetaDataImport:: EnumTypeDefs metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 28bd06b70573b780b687da9de0e13e17c29bb39a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670692"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="e10f2-103">IMetaDataImport::EnumTypeDefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e10f2-103">IMetaDataImport::EnumTypeDefs Method</span></span>

<span data-ttu-id="e10f2-104">Geçerli kapsam içindeki tüm türleri temsil eden TypeDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e10f2-104">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e10f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e10f2-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e10f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e10f2-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="e10f2-107">dışı Yeni Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e10f2-107">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="e10f2-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e10f2-108">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="e10f2-109">'ndaki TypeDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="e10f2-109">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e10f2-110">'ndaki Dizinin en büyük boyutu `rTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="e10f2-110">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="e10f2-111">dışı İçinde döndürülen TypeDef belirteçleri sayısı `rTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="e10f2-111">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e10f2-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e10f2-112">Return Value</span></span>  
  
|<span data-ttu-id="e10f2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e10f2-113">HRESULT</span></span>|<span data-ttu-id="e10f2-114">Description</span><span class="sxs-lookup"><span data-stu-id="e10f2-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e10f2-115">`EnumTypeDefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e10f2-115">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e10f2-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="e10f2-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="e10f2-117">Bu durumda, `pcTypeDefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e10f2-117">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e10f2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e10f2-118">Remarks</span></span>  

 <span data-ttu-id="e10f2-119">TypeDef belirteci, bir sınıf veya arabirim gibi bir türü ve bir genişletilebilirlik mekanizması aracılığıyla eklenen herhangi bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e10f2-119">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e10f2-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e10f2-120">Requirements</span></span>  

 <span data-ttu-id="e10f2-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e10f2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e10f2-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e10f2-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e10f2-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e10f2-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e10f2-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e10f2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e10f2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e10f2-125">See also</span></span>

- [<span data-ttu-id="e10f2-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e10f2-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e10f2-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e10f2-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
