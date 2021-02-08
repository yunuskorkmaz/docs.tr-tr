---
description: ': IMetaDataImport:: EnumUserStrings yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumUserStrings Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: a4ead696f3d924fef9ebfed5c4f1eb97eb13e14e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799323"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="be828-103">IMetaDataImport::EnumUserStrings Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be828-103">IMetaDataImport::EnumUserStrings Method</span></span>

<span data-ttu-id="be828-104">Geçerli meta veri kapsamındaki sabit kodlanmış dizeleri temsil eden dize belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="be828-104">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be828-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be828-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be828-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be828-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="be828-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be828-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="be828-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="be828-108">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="be828-109">dışı Dize belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="be828-109">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="be828-110">'ndaki Dizinin en büyük boyutu `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="be828-110">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="be828-111">dışı İçinde döndürülen dize belirteçleri sayısı `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="be828-111">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be828-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be828-112">Return Value</span></span>  
  
|<span data-ttu-id="be828-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be828-113">HRESULT</span></span>|<span data-ttu-id="be828-114">Description</span><span class="sxs-lookup"><span data-stu-id="be828-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="be828-115">`EnumUserStrings` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="be828-115">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="be828-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="be828-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="be828-117">Bu durumda, `pcStrings` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="be828-117">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be828-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be828-118">Remarks</span></span>  

 <span data-ttu-id="be828-119">Dize belirteçleri [ımetadatayayma::D efineUserString](imetadataemit-defineuserstring-method.md) yöntemi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="be828-119">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="be828-120">Bu yöntem, bir derleyici yerine bir meta veri tarayıcısı tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="be828-120">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be828-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be828-121">Requirements</span></span>  

 <span data-ttu-id="be828-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be828-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be828-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be828-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be828-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="be828-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be828-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be828-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be828-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be828-126">See also</span></span>

- [<span data-ttu-id="be828-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be828-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="be828-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be828-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
