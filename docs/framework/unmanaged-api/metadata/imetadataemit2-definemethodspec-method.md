---
description: 'Hakkında daha fazla bilgi edinin: IMetaDataEmit2::D efineMethodSpec yöntemi'
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
ms.openlocfilehash: 4b5283375ba194a86a83b142b3b2bdc06bfd35da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745742"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="dac52-103">IMetaDataEmit2::DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dac52-103">IMetaDataEmit2::DefineMethodSpec Method</span></span>

<span data-ttu-id="dac52-104">Bir yönteminin genel bir örneğini oluşturur ve tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="dac52-104">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac52-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dac52-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dac52-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dac52-106">Parameters</span></span>  

 `tkParent`  
 <span data-ttu-id="dac52-107">'ndaki Genel örneğin oluşturulacağı yöntemi için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="dac52-107">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="dac52-108">Belirtecin veya türünde olması gerekir `mdMethodDef` `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="dac52-108">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="dac52-109">'ndaki Metodun ikili COM+ imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dac52-109">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="dac52-110">'ndaki Bayt cinsinden boyutu `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="dac52-110">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="dac52-111">dışı Metodun meta veri imza tanımına belirteç.</span><span class="sxs-lookup"><span data-stu-id="dac52-111">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac52-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dac52-112">Requirements</span></span>  

 <span data-ttu-id="dac52-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dac52-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dac52-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dac52-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dac52-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dac52-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dac52-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dac52-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac52-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dac52-117">See also</span></span>

- [<span data-ttu-id="dac52-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dac52-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="dac52-119">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dac52-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
