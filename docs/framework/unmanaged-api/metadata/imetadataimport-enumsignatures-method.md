---
title: IMetaDataImport::EnumSignatures Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 3021124184ab0491337a07144e6f77b5bfea3681
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721978"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="541a3-102">IMetaDataImport::EnumSignatures Yöntemi</span><span class="sxs-lookup"><span data-stu-id="541a3-102">IMetaDataImport::EnumSignatures Method</span></span>

<span data-ttu-id="541a3-103">Geçerli kapsamdaki tek başına imzaları temsil eden Imza belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="541a3-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="541a3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="541a3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="541a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="541a3-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="541a3-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="541a3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="541a3-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="541a3-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="541a3-108">dışı Imza belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="541a3-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="541a3-109">'ndaki Dizinin en büyük boyutu `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="541a3-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="541a3-110">dışı İçinde döndürülen Imza belirteçleri sayısı `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="541a3-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="541a3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="541a3-111">Return Value</span></span>  
  
|<span data-ttu-id="541a3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="541a3-112">HRESULT</span></span>|<span data-ttu-id="541a3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="541a3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="541a3-114">`EnumSignatures` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="541a3-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="541a3-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="541a3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="541a3-116">Bu durumda, `pcSignatures` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="541a3-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="541a3-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="541a3-117">Remarks</span></span>  

 <span data-ttu-id="541a3-118">Imza belirteçleri [ımetadatayayma:: GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) yöntemi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="541a3-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="541a3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="541a3-119">Requirements</span></span>  

 <span data-ttu-id="541a3-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="541a3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="541a3-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="541a3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="541a3-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="541a3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="541a3-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="541a3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541a3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="541a3-124">See also</span></span>

- [<span data-ttu-id="541a3-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="541a3-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="541a3-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="541a3-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
