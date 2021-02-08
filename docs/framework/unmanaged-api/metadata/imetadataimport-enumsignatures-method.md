---
description: ': IMetaDataImport:: Enumimzalara metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ed41dd42151791e3d27950f30b10d91217ad7e7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771632"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="045b8-103">IMetaDataImport::EnumSignatures Yöntemi</span><span class="sxs-lookup"><span data-stu-id="045b8-103">IMetaDataImport::EnumSignatures Method</span></span>

<span data-ttu-id="045b8-104">Geçerli kapsamdaki tek başına imzaları temsil eden Imza belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="045b8-104">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="045b8-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="045b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="045b8-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="045b8-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="045b8-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="045b8-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="045b8-108">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="045b8-109">dışı Imza belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="045b8-109">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="045b8-110">'ndaki Dizinin en büyük boyutu `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="045b8-110">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="045b8-111">dışı İçinde döndürülen Imza belirteçleri sayısı `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="045b8-111">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="045b8-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="045b8-112">Return Value</span></span>  
  
|<span data-ttu-id="045b8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="045b8-113">HRESULT</span></span>|<span data-ttu-id="045b8-114">Description</span><span class="sxs-lookup"><span data-stu-id="045b8-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="045b8-115">`EnumSignatures` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="045b8-115">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="045b8-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="045b8-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="045b8-117">Bu durumda, `pcSignatures` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="045b8-117">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="045b8-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="045b8-118">Remarks</span></span>  

 <span data-ttu-id="045b8-119">Imza belirteçleri [ımetadatayayma:: GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) yöntemi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="045b8-119">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="045b8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="045b8-120">Requirements</span></span>  

 <span data-ttu-id="045b8-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="045b8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="045b8-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="045b8-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="045b8-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="045b8-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="045b8-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="045b8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045b8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="045b8-125">See also</span></span>

- [<span data-ttu-id="045b8-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="045b8-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="045b8-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="045b8-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
