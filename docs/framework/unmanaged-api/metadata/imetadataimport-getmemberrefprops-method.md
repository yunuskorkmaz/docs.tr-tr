---
title: IMetaDataImport::GetMemberRefProps Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ac0d77b1d8d35a7753d3a501f147bd5ac53750c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583736"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="78995-102">IMetaDataImport::GetMemberRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="78995-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="78995-103">Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="78995-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78995-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78995-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="78995-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78995-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="78995-106">[in] İlişkili meta verileri için döndürülecek MemberRef belirteç.</span><span class="sxs-lookup"><span data-stu-id="78995-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="78995-107">[out] Üye ya da üyeye ya da üye temsil eden bir MethodDef bildirir modül sınıfı temsil eden bir ModuleRef belirteci bildiren sınıfın temsil ettiği bir TypeDef veya TypeRef veya TypeSpec'te belirteci.</span><span class="sxs-lookup"><span data-stu-id="78995-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="78995-108">[out] Üyenin adını bir dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="78995-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="78995-109">[in] Geniş karakter cinsinden istenen boyuta `szMember`.</span><span class="sxs-lookup"><span data-stu-id="78995-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="78995-110">[out] Geniş karakter cinsinden döndürülen boyutu `szMember`.</span><span class="sxs-lookup"><span data-stu-id="78995-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="78995-111">[out] İkili meta veri imzası üyesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="78995-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="78995-112">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="78995-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78995-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78995-113">Requirements</span></span>  
 <span data-ttu-id="78995-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78995-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78995-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="78995-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78995-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="78995-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78995-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78995-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78995-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78995-118">See also</span></span>
- [<span data-ttu-id="78995-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78995-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="78995-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78995-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
