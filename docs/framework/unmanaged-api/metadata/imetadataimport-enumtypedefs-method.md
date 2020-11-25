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
ms.openlocfilehash: 4545f5f8d78e588c655a72340210a785b0feb619
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720418"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="d6fc6-102">IMetaDataImport::EnumTypeDefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6fc6-102">IMetaDataImport::EnumTypeDefs Method</span></span>

<span data-ttu-id="d6fc6-103">Geçerli kapsam içindeki tüm türleri temsil eden TypeDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6fc6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d6fc6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6fc6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6fc6-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="d6fc6-106">dışı Yeni Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="d6fc6-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="d6fc6-108">'ndaki TypeDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d6fc6-109">'ndaki Dizinin en büyük boyutu `rTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="d6fc6-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="d6fc6-110">dışı İçinde döndürülen TypeDef belirteçleri sayısı `rTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="d6fc6-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6fc6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d6fc6-111">Return Value</span></span>  
  
|<span data-ttu-id="d6fc6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6fc6-112">HRESULT</span></span>|<span data-ttu-id="d6fc6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6fc6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d6fc6-114">`EnumTypeDefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d6fc6-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d6fc6-116">Bu durumda, `pcTypeDefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6fc6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6fc6-117">Remarks</span></span>  

 <span data-ttu-id="d6fc6-118">TypeDef belirteci, bir sınıf veya arabirim gibi bir türü ve bir genişletilebilirlik mekanizması aracılığıyla eklenen herhangi bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6fc6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6fc6-119">Requirements</span></span>  

 <span data-ttu-id="d6fc6-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6fc6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6fc6-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d6fc6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6fc6-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d6fc6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6fc6-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6fc6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fc6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6fc6-124">See also</span></span>

- [<span data-ttu-id="d6fc6-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6fc6-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d6fc6-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6fc6-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
