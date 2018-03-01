---
title: IMetaDataImport::GetMemberRefProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6cd229d9286dfe9c12a4c6f7e171f8bb634fcc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="928c7-102">IMetaDataImport::GetMemberRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="928c7-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="928c7-103">Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="928c7-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="928c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="928c7-104">Syntax</span></span>  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="928c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="928c7-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="928c7-106">[in] İlişkili meta verileri döndürmek için MemberRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="928c7-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="928c7-107">[out] Üye veya üye veya üye temsil eden bir MethodDef bildirir modülü sınıfın temsil ettiği ModuleRef belirteci bildirir sınıfı temsil eden bir TypeDef veya TypeRef veya TypeSpec'te belirteci.</span><span class="sxs-lookup"><span data-stu-id="928c7-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="928c7-108">[out] Üyenin adı için string buffer.</span><span class="sxs-lookup"><span data-stu-id="928c7-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="928c7-109">[in] Geniş karakterler istenen boyutta `szMember`.</span><span class="sxs-lookup"><span data-stu-id="928c7-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="928c7-110">[out] Geniş karakterler döndürülen boyutu `szMember`.</span><span class="sxs-lookup"><span data-stu-id="928c7-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="928c7-111">[out] Üye için ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="928c7-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="928c7-112">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="928c7-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="928c7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="928c7-113">Requirements</span></span>  
 <span data-ttu-id="928c7-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="928c7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="928c7-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="928c7-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="928c7-116">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="928c7-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="928c7-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="928c7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="928c7-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="928c7-118">See Also</span></span>  
 [<span data-ttu-id="928c7-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="928c7-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="928c7-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="928c7-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
