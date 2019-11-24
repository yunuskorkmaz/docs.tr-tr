---
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
ms.openlocfilehash: ed193aab8beb0de1321aa1d52ec9f963b08b316c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441668"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="fa476-102">IMetaDataImport::EnumMembersWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa476-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="fa476-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span><span class="sxs-lookup"><span data-stu-id="fa476-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa476-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa476-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fa476-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa476-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fa476-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="fa476-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="fa476-107">[in] A TypeDef token representing the type with members to enumerate.</span><span class="sxs-lookup"><span data-stu-id="fa476-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="fa476-108">[in] The member name that limits the scope of the enumerator.</span><span class="sxs-lookup"><span data-stu-id="fa476-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="fa476-109">[out] The array used to store the MemberDef tokens.</span><span class="sxs-lookup"><span data-stu-id="fa476-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fa476-110">[in] The maximum size of the `rMembers` array.</span><span class="sxs-lookup"><span data-stu-id="fa476-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="fa476-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="fa476-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa476-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa476-112">Remarks</span></span>  
 <span data-ttu-id="fa476-113">This method enumerates fields and methods, but not properties or events.</span><span class="sxs-lookup"><span data-stu-id="fa476-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="fa476-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span><span class="sxs-lookup"><span data-stu-id="fa476-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa476-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa476-115">Return Value</span></span>  
  
|<span data-ttu-id="fa476-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa476-116">HRESULT</span></span>|<span data-ttu-id="fa476-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa476-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fa476-118">`EnumTypeDefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="fa476-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fa476-119">There are no MemberDef tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="fa476-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="fa476-120">In that case, `pcTokens` is zero.</span><span class="sxs-lookup"><span data-stu-id="fa476-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa476-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa476-121">Requirements</span></span>  
 <span data-ttu-id="fa476-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa476-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa476-123">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa476-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa476-124">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa476-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa476-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa476-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa476-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa476-126">See also</span></span>

- [<span data-ttu-id="fa476-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa476-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fa476-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa476-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
