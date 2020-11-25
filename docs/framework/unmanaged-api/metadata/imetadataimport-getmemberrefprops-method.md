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
ms.openlocfilehash: 3237b67f8f711e9ef213d6fc66f1513c534fbdeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733210"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="e1704-102">IMetaDataImport::GetMemberRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1704-102">IMetaDataImport::GetMemberRefProps Method</span></span>

<span data-ttu-id="e1704-103">Belirtilen belirteç tarafından başvurulan üyeyle ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="e1704-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1704-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e1704-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e1704-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1704-105">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="e1704-106">'ndaki İçin ilişkili meta verileri döndürecek MemberRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="e1704-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="e1704-107">dışı Üyeyi bildiren sınıfı temsil eden bir TypeDef veya TypeRef, ya da üyeyi bildiren modül sınıfını temsil eden bir ModuleRef belirteci ya da üyeyi temsil eden bir MethodDef.</span><span class="sxs-lookup"><span data-stu-id="e1704-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="e1704-108">dışı Üyenin adı için bir dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="e1704-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="e1704-109">'ndaki Geniş karakterdeki istenen boyut `szMember` .</span><span class="sxs-lookup"><span data-stu-id="e1704-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="e1704-110">dışı Geniş karakter olarak döndürülen boyut `szMember` .</span><span class="sxs-lookup"><span data-stu-id="e1704-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="e1704-111">dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1704-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="e1704-112">dışı Bayt cinsinden boyut `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="e1704-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1704-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1704-113">Requirements</span></span>  

 <span data-ttu-id="e1704-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1704-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1704-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e1704-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1704-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e1704-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1704-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1704-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1704-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1704-118">See also</span></span>

- [<span data-ttu-id="e1704-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1704-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e1704-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1704-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
