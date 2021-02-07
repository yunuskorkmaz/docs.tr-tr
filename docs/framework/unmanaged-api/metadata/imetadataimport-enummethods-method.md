---
description: ': IMetaDataImport:: EnumMethods yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumMethods Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 4fce3593d088a8d401335869eb49e598ac4c3fd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670686"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="bccac-103">IMetaDataImport::EnumMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bccac-103">IMetaDataImport::EnumMethods Method</span></span>

<span data-ttu-id="bccac-104">Belirtilen türdeki yöntemleri temsil eden MethodDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="bccac-104">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bccac-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bccac-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bccac-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="bccac-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bccac-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bccac-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bccac-108">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="bccac-109">'ndaki Numaralandırılacak yöntemleri içeren türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="bccac-109">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="bccac-110">dışı MethodDef belirteçlerini depolayacak dizi.</span><span class="sxs-lookup"><span data-stu-id="bccac-110">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bccac-111">'ndaki MethodDef dizisinin en büyük boyutu `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="bccac-111">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bccac-112">dışı İçinde döndürülen MethodDef belirteçleri sayısı `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="bccac-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bccac-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bccac-113">Return Value</span></span>  
  
|<span data-ttu-id="bccac-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bccac-114">HRESULT</span></span>|<span data-ttu-id="bccac-115">Description</span><span class="sxs-lookup"><span data-stu-id="bccac-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bccac-116">`EnumMethods` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bccac-116">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bccac-117">Numaralandırılacak bir MethodDef belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="bccac-117">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="bccac-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="bccac-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bccac-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bccac-119">Requirements</span></span>  

 <span data-ttu-id="bccac-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bccac-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccac-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bccac-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bccac-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bccac-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bccac-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccac-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccac-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bccac-124">See also</span></span>

- [<span data-ttu-id="bccac-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bccac-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="bccac-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bccac-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
