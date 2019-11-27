---
title: IMetaDataImport::EnumParams Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: e5fa3647c86d97730e7ad6a2576dd34af75251d6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433950"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="ac40d-102">IMetaDataImport::EnumParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac40d-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="ac40d-103">Belirtilen MethodDef belirtecinin başvurduğu metodun parametrelerini temsil eden ParamDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ac40d-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac40d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac40d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac40d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac40d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ac40d-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac40d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ac40d-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac40d-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="ac40d-108">'ndaki Numaralandırılacak parametrelere sahip yöntemi temsil eden bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="ac40d-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="ac40d-109">dışı ParamDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="ac40d-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ac40d-110">'ndaki `rParams` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac40d-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ac40d-111">dışı `rParams`' de döndürülen ParamDef belirteçleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="ac40d-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac40d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac40d-112">Return Value</span></span>  
  
|<span data-ttu-id="ac40d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac40d-113">HRESULT</span></span>|<span data-ttu-id="ac40d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac40d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ac40d-115">`EnumParams` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ac40d-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ac40d-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="ac40d-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="ac40d-117">Bu durumda `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="ac40d-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac40d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac40d-118">Requirements</span></span>  
 <span data-ttu-id="ac40d-119">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac40d-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac40d-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ac40d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac40d-121">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ac40d-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac40d-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac40d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac40d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac40d-123">See also</span></span>

- [<span data-ttu-id="ac40d-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac40d-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ac40d-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac40d-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
