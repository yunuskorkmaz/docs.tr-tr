---
description: ': IMetaDataImport:: EnumTypeSpecs yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumTypeSpecs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 7446bbf3296ffb6cfa3a20f594b4a7da22acff5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799349"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="2dd13-103">IMetaDataImport::EnumTypeSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2dd13-103">IMetaDataImport::EnumTypeSpecs Method</span></span>

<span data-ttu-id="2dd13-104">Geçerli meta veri kapsamında tanımlanan TypeSpec belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2dd13-104">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dd13-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2dd13-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dd13-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2dd13-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="2dd13-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2dd13-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2dd13-108">Bu yöntemin ilk çağrısı için bu değer NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dd13-108">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="2dd13-109">dışı TypeSpec belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="2dd13-109">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2dd13-110">'ndaki Dizinin en büyük boyutu `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="2dd13-110">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="2dd13-111">dışı İçinde döndürülen TypeSpec belirteçleri sayısı `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="2dd13-111">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dd13-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2dd13-112">Return Value</span></span>  
  
|<span data-ttu-id="2dd13-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2dd13-113">HRESULT</span></span>|<span data-ttu-id="2dd13-114">Description</span><span class="sxs-lookup"><span data-stu-id="2dd13-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2dd13-115">`EnumTypeSpecs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2dd13-115">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2dd13-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="2dd13-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="2dd13-117">Bu durumda, `pcTypeSpecs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2dd13-117">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dd13-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2dd13-118">Remarks</span></span>  

 <span data-ttu-id="2dd13-119">TypeSpec belirteçleri [ımetadatayayma:: GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) yöntemi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2dd13-119">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dd13-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2dd13-120">Requirements</span></span>  

 <span data-ttu-id="2dd13-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dd13-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dd13-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2dd13-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2dd13-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2dd13-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2dd13-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dd13-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd13-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dd13-125">See also</span></span>

- [<span data-ttu-id="2dd13-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2dd13-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2dd13-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2dd13-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
