---
description: ': IMetaDataImport:: EnumMethodsWithName yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumMethodsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b77fc15bd7752b5b6b2b95d66a6bf04518616884
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745612"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="64952-103">IMetaDataImport::EnumMethodsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64952-103">IMetaDataImport::EnumMethodsWithName Method</span></span>

<span data-ttu-id="64952-104">Belirtilen ada sahip olan ve belirtilen TypeDef belirtecinin başvurduğu tür tarafından tanımlanan yöntemleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="64952-104">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64952-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64952-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64952-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64952-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="64952-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64952-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="64952-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64952-108">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="64952-109">'ndaki Yöntemlerini Numaralandırılacak türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="64952-109">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="64952-110">'ndaki Sabit listesinin kapsamını sınırlayan ad.</span><span class="sxs-lookup"><span data-stu-id="64952-110">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="64952-111">dışı MethodDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="64952-111">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="64952-112">'ndaki Dizinin en büyük boyutu `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="64952-112">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="64952-113">dışı İçinde döndürülen MethodDef belirteçleri sayısı `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="64952-113">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64952-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64952-114">Remarks</span></span>  

 <span data-ttu-id="64952-115">Bu yöntem, alanları ve yöntemleri numaralandırır, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="64952-115">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="64952-116">[IMetaDataImport:: EnumMethods](imetadataimport-enummethods-method.md)'ın aksine, `EnumMethodsWithName` belirtilen ada sahip olmayan tüm metot belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="64952-116">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64952-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64952-117">Return Value</span></span>  
  
|<span data-ttu-id="64952-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64952-118">HRESULT</span></span>|<span data-ttu-id="64952-119">Description</span><span class="sxs-lookup"><span data-stu-id="64952-119">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="64952-120">`EnumMethodsWithName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="64952-120">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="64952-121">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="64952-121">There are no tokens to enumerate.</span></span> <span data-ttu-id="64952-122">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="64952-122">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64952-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64952-123">Requirements</span></span>  

 <span data-ttu-id="64952-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64952-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64952-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64952-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64952-126">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="64952-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64952-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64952-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64952-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64952-128">See also</span></span>

- [<span data-ttu-id="64952-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64952-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="64952-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64952-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
