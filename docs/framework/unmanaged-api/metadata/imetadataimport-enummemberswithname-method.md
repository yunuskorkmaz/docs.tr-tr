---
description: ': IMetaDataImport:: EnumMembersWithName metodu hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumMembersWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: bb6d8f0769029dccaf1f52dd211c67d47bf32a73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670768"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="e48e0-103">IMetaDataImport::EnumMembersWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e48e0-103">IMetaDataImport::EnumMembersWithName Method</span></span>

<span data-ttu-id="e48e0-104">Belirtilen ada sahip belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e48e0-104">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e48e0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e48e0-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e48e0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e48e0-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="e48e0-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e48e0-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="e48e0-108">'ndaki Numaralandırılacak üyeleri olan türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="e48e0-108">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="e48e0-109">'ndaki Numaralandırıcı kapsamını sınırlayan üye adı.</span><span class="sxs-lookup"><span data-stu-id="e48e0-109">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="e48e0-110">dışı MemberDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="e48e0-110">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e48e0-111">'ndaki Dizinin en büyük boyutu `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="e48e0-111">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e48e0-112">dışı İçinde döndürülen MemberDef belirteçlerinin gerçek sayısı `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="e48e0-112">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e48e0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e48e0-113">Remarks</span></span>  

 <span data-ttu-id="e48e0-114">Bu yöntem, alanları ve yöntemleri numaralandırır, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e48e0-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="e48e0-115">[IMetaDataImport:: EnumMembers](imetadataimport-enummembers-method.md)'ın aksine, `EnumMembersWithName` belirtilen ada sahip olmayan tüm alan ve üye belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="e48e0-115">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e48e0-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e48e0-116">Return Value</span></span>  
  
|<span data-ttu-id="e48e0-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e48e0-117">HRESULT</span></span>|<span data-ttu-id="e48e0-118">Description</span><span class="sxs-lookup"><span data-stu-id="e48e0-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e48e0-119">`EnumTypeDefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e48e0-119">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e48e0-120">Numaralandırılacak MemberDef belirteçleri yok.</span><span class="sxs-lookup"><span data-stu-id="e48e0-120">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="e48e0-121">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e48e0-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e48e0-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e48e0-122">Requirements</span></span>  

 <span data-ttu-id="e48e0-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e48e0-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e48e0-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e48e0-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e48e0-125">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e48e0-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e48e0-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48e0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48e0-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e48e0-127">See also</span></span>

- [<span data-ttu-id="e48e0-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e48e0-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e48e0-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e48e0-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
