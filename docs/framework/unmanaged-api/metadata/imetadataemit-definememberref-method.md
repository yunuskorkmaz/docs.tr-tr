---
title: IMetaDataEmit::DefineMemberRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38e4928ad0f3560698cbecab81a11630d67e4db2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777619"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="3c5cf-102">IMetaDataEmit::DefineMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c5cf-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="3c5cf-103">Geçerli kapsam dışında bir modül üyesi başvuru tanımlar ve bu başvuru tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="3c5cf-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c5cf-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c5cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c5cf-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="3c5cf-106">[in] Belirteci için hedef üyenin sınıf veya arabirim üyesi genel olmadığından, Genel üyesiyse `mdModuleRef` söz konusu diğer dosya için belirteç.</span><span class="sxs-lookup"><span data-stu-id="3c5cf-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="3c5cf-107">[in] Hedef üyesinin adı.</span><span class="sxs-lookup"><span data-stu-id="3c5cf-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3c5cf-108">[in] Hedef üye imzası.</span><span class="sxs-lookup"><span data-stu-id="3c5cf-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3c5cf-109">[in] Bayt sayısı `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3c5cf-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="3c5cf-110">[out] `mdMemberRef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="3c5cf-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c5cf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c5cf-111">Requirements</span></span>  
 <span data-ttu-id="3c5cf-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c5cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c5cf-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3c5cf-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c5cf-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3c5cf-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c5cf-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c5cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c5cf-116">See also</span></span>

- [<span data-ttu-id="3c5cf-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c5cf-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3c5cf-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c5cf-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
