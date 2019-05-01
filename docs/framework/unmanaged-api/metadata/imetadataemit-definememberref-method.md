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
ms.openlocfilehash: d5d386b1d3f95e703cc5d9ad1353ea6b84b5b455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043231"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="fd723-102">IMetaDataEmit::DefineMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd723-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="fd723-103">Geçerli kapsam dışında bir modül üyesi başvuru tanımlar ve bu başvuru tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="fd723-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd723-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd723-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd723-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd723-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="fd723-106">[in] Belirteci için hedef üyenin sınıf veya arabirim üyesi genel olmadığından, Genel üyesiyse `mdModuleRef` söz konusu diğer dosya için belirteç.</span><span class="sxs-lookup"><span data-stu-id="fd723-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="fd723-107">[in] Hedef üyesinin adı.</span><span class="sxs-lookup"><span data-stu-id="fd723-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fd723-108">[in] Hedef üye imzası.</span><span class="sxs-lookup"><span data-stu-id="fd723-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fd723-109">[in] Bayt sayısı `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fd723-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="fd723-110">[out] `mdMemberRef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="fd723-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd723-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd723-111">Requirements</span></span>  
 <span data-ttu-id="fd723-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd723-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd723-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fd723-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd723-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="fd723-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd723-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd723-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd723-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd723-116">See also</span></span>

- [<span data-ttu-id="fd723-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd723-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fd723-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd723-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
