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
ms.openlocfilehash: 817b3a18b047bfca1f3a7c7099920a12e6253f58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712839"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="22490-102">IMetaDataEmit2::DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22490-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>

<span data-ttu-id="22490-103">Bir yönteminin genel bir örneğini oluşturur ve tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="22490-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22490-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="22490-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22490-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22490-105">Parameters</span></span>  

 `tkParent`  
 <span data-ttu-id="22490-106">'ndaki Genel örneğin oluşturulacağı yöntemi için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="22490-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="22490-107">Belirtecin veya türünde olması gerekir `mdMethodDef` `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="22490-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="22490-108">'ndaki Metodun ikili COM+ imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22490-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="22490-109">'ndaki Bayt cinsinden boyutu `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="22490-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="22490-110">dışı Metodun meta veri imza tanımına belirteç.</span><span class="sxs-lookup"><span data-stu-id="22490-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22490-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22490-111">Requirements</span></span>  

 <span data-ttu-id="22490-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22490-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22490-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="22490-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22490-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="22490-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22490-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22490-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22490-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22490-116">See also</span></span>

- [<span data-ttu-id="22490-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22490-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="22490-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22490-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
