---
title: IMetaDataImport::GetMemberRefProps Yöntemi
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
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175375"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="217ea-102">IMetaDataImport::GetMemberRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="217ea-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="217ea-103">Belirtilen belirteç tarafından başvurulan üye ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="217ea-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="217ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="217ea-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="217ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="217ea-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="217ea-106">[içinde] ÜyeRef belirteç için ilişkili meta verileri döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="217ea-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="217ea-107">[çıkış] Üyeyi bildiren sınıfı temsil eden bir TypeDef veya TypeRef veya TypeSpec belirteci veya üyeyi bildiren modül sınıfını temsil eden bir ModuleRef belirteci veya üyeyi temsil eden bir MethodDef belirteç.</span><span class="sxs-lookup"><span data-stu-id="217ea-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="217ea-108">[çıkış] Üyenin adı için bir dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="217ea-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="217ea-109">[içinde] Geniş karakterlerde istenen `szMember`boyut.</span><span class="sxs-lookup"><span data-stu-id="217ea-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="217ea-110">[çıkış] Döndürülen boyut geniş karakterler `szMember`.</span><span class="sxs-lookup"><span data-stu-id="217ea-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="217ea-111">[çıkış] Üye için ikili meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="217ea-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="217ea-112">[çıkış] `ppvSigBlob`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="217ea-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="217ea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="217ea-113">Requirements</span></span>  
 <span data-ttu-id="217ea-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="217ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="217ea-115">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="217ea-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="217ea-116">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="217ea-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="217ea-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="217ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217ea-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="217ea-118">See also</span></span>

- [<span data-ttu-id="217ea-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="217ea-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="217ea-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="217ea-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
