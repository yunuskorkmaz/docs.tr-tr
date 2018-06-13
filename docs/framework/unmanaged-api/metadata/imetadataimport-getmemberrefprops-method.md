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
ms.openlocfilehash: 0d62b9be1bef16014e2870c15a232bb46d4daf10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448760"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="63265-102">IMetaDataImport::GetMemberRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="63265-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="63265-103">Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="63265-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63265-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63265-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="63265-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63265-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="63265-106">[in] İlişkili meta verileri döndürmek için MemberRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="63265-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="63265-107">[out] Üye veya üye veya üye temsil eden bir MethodDef bildirir modülü sınıfın temsil ettiği ModuleRef belirteci bildirir sınıfı temsil eden bir TypeDef veya TypeRef veya TypeSpec'te belirteci.</span><span class="sxs-lookup"><span data-stu-id="63265-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="63265-108">[out] Üyenin adı için string buffer.</span><span class="sxs-lookup"><span data-stu-id="63265-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="63265-109">[in] Geniş karakterler istenen boyutta `szMember`.</span><span class="sxs-lookup"><span data-stu-id="63265-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="63265-110">[out] Geniş karakterler döndürülen boyutu `szMember`.</span><span class="sxs-lookup"><span data-stu-id="63265-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="63265-111">[out] Üye için ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63265-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="63265-112">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="63265-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63265-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63265-113">Requirements</span></span>  
 <span data-ttu-id="63265-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63265-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63265-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="63265-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63265-116">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="63265-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63265-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63265-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63265-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63265-118">See Also</span></span>  
 [<span data-ttu-id="63265-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63265-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="63265-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63265-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
