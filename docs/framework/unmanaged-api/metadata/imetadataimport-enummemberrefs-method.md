---
description: ': IMetaDataImport:: EnumMemberRefs metodu hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumMemberRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: 0c9b10342f73ae5b604ac25b6ff8ccec58deb5ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670950"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="57906-103">IMetaDataImport::EnumMemberRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57906-103">IMetaDataImport::EnumMemberRefs Method</span></span>

<span data-ttu-id="57906-104">Belirtilen türdeki üyeleri temsil eden MemberRef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="57906-104">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57906-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57906-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57906-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57906-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="57906-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57906-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="57906-108">'ndaki Üyeleri numaralandırılmış olan tür için bir TypeDef, TypeRef, MethodDef veya ModuleRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="57906-108">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="57906-109">dışı MemberRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="57906-109">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="57906-110">'ndaki Dizinin en büyük boyutu `rMemberRefs` .</span><span class="sxs-lookup"><span data-stu-id="57906-110">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="57906-111">dışı İçinde döndürülen MemberRef belirteçleri gerçek sayısı `rMemberRefs` .</span><span class="sxs-lookup"><span data-stu-id="57906-111">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57906-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57906-112">Return Value</span></span>  
  
|<span data-ttu-id="57906-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57906-113">HRESULT</span></span>|<span data-ttu-id="57906-114">Description</span><span class="sxs-lookup"><span data-stu-id="57906-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="57906-115">`EnumMemberRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="57906-115">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="57906-116">Numaralandırılacak bir MemberRef belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="57906-116">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="57906-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="57906-117">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57906-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57906-118">Requirements</span></span>  

 <span data-ttu-id="57906-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57906-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57906-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="57906-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57906-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="57906-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57906-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57906-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57906-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57906-123">See also</span></span>

- [<span data-ttu-id="57906-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57906-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="57906-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57906-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
