---
title: IMetaDataEmit2::DefineMethodSpec Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d56209e030939f53e3f72fe0c8a10db2160dd19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492526"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="9c7d8-102">IMetaDataEmit2::DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c7d8-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="9c7d8-103">Bir yöntem genel bir örneğini oluşturur ve tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="9c7d8-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c7d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c7d8-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c7d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c7d8-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="9c7d8-106">[in] Genel örnek oluşturulacağı yöntemi için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="9c7d8-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="9c7d8-107">Belirteç türü olmalıdır `mdMethodDef` veya `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="9c7d8-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9c7d8-108">[in] İkili COM + metodun imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9c7d8-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="9c7d8-109">[in] Bayt cinsinden boyutu, `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9c7d8-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="9c7d8-110">[out] Yöntemin meta veri imzası tanımı için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="9c7d8-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c7d8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c7d8-111">Requirements</span></span>  
 <span data-ttu-id="9c7d8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c7d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c7d8-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9c7d8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c7d8-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="9c7d8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c7d8-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c7d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c7d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c7d8-116">See also</span></span>
- [<span data-ttu-id="9c7d8-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c7d8-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="9c7d8-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c7d8-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
