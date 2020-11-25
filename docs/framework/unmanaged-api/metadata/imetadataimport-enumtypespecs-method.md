---
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
ms.openlocfilehash: 38c9f8df12b0fc83a236d2cb7c32d1198be7096d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719820"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="f3fd9-102">IMetaDataImport::EnumTypeSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3fd9-102">IMetaDataImport::EnumTypeSpecs Method</span></span>

<span data-ttu-id="f3fd9-103">Geçerli meta veri kapsamında tanımlanan TypeSpec belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fd9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f3fd9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3fd9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3fd9-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="f3fd9-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f3fd9-107">Bu yöntemin ilk çağrısı için bu değer NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="f3fd9-108">dışı TypeSpec belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f3fd9-109">'ndaki Dizinin en büyük boyutu `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="f3fd9-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="f3fd9-110">dışı İçinde döndürülen TypeSpec belirteçleri sayısı `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="f3fd9-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3fd9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f3fd9-111">Return Value</span></span>  
  
|<span data-ttu-id="f3fd9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3fd9-112">HRESULT</span></span>|<span data-ttu-id="f3fd9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3fd9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f3fd9-114">`EnumTypeSpecs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f3fd9-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f3fd9-116">Bu durumda, `pcTypeSpecs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3fd9-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3fd9-117">Remarks</span></span>  

 <span data-ttu-id="f3fd9-118">TypeSpec belirteçleri [ımetadatayayma:: GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) yöntemi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fd9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3fd9-119">Requirements</span></span>  

 <span data-ttu-id="f3fd9-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3fd9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fd9-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3fd9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3fd9-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f3fd9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3fd9-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fd9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fd9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3fd9-124">See also</span></span>

- [<span data-ttu-id="f3fd9-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3fd9-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f3fd9-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3fd9-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
