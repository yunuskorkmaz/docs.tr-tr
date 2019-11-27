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
ms.openlocfilehash: 1d6d66ea62cbf679f722f830b3638455001aedd6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437495"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="a414f-102">IMetaDataImport::GetMemberRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a414f-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="a414f-103">Belirtilen belirteç tarafından başvurulan üyeyle ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="a414f-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a414f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a414f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a414f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a414f-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="a414f-106">'ndaki İçin ilişkili meta verileri döndürecek MemberRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="a414f-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="a414f-107">dışı Üyeyi bildiren sınıfı temsil eden bir TypeDef veya TypeRef, ya da üyeyi bildiren modül sınıfını temsil eden bir ModuleRef belirteci ya da üyeyi temsil eden bir MethodDef.</span><span class="sxs-lookup"><span data-stu-id="a414f-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="a414f-108">dışı Üyenin adı için bir dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="a414f-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="a414f-109">'ndaki `szMember`geniş karakterdeki istenen boyut.</span><span class="sxs-lookup"><span data-stu-id="a414f-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="a414f-110">dışı `szMember`geniş karakterdeki döndürülen boyut.</span><span class="sxs-lookup"><span data-stu-id="a414f-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="a414f-111">dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a414f-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="a414f-112">dışı `ppvSigBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a414f-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a414f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a414f-113">Requirements</span></span>  
 <span data-ttu-id="a414f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a414f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a414f-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a414f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a414f-116">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a414f-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a414f-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a414f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a414f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a414f-118">See also</span></span>

- [<span data-ttu-id="a414f-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a414f-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a414f-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a414f-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
