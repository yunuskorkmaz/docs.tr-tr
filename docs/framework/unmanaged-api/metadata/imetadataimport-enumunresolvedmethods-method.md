---
description: ': IMetaDataImport:: EnumUnresolvedMethods yöntemi hakkında daha fazla bilgi'
title: IMetaDataImport::EnumUnresolvedMethods Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: e894ecdde91a2263783234d73fa50d890a13e413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799336"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="4bba8-103">IMetaDataImport::EnumUnresolvedMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bba8-103">IMetaDataImport::EnumUnresolvedMethods Method</span></span>

<span data-ttu-id="4bba8-104">Geçerli meta veri kapsamındaki çözümlenmemiş yöntemleri temsil eden MemberDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="4bba8-104">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bba8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bba8-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bba8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bba8-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="4bba8-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4bba8-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4bba8-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4bba8-108">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="4bba8-109">dışı MemberDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="4bba8-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4bba8-110">'ndaki Dizinin en büyük boyutu `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="4bba8-110">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4bba8-111">dışı İçinde döndürülen MemberDef belirteçleri sayısı `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="4bba8-111">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bba8-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4bba8-112">Return Value</span></span>  
  
|<span data-ttu-id="4bba8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bba8-113">HRESULT</span></span>|<span data-ttu-id="4bba8-114">Description</span><span class="sxs-lookup"><span data-stu-id="4bba8-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4bba8-115">`EnumUnresolvedMethods` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4bba8-115">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4bba8-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="4bba8-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="4bba8-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="4bba8-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bba8-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bba8-118">Remarks</span></span>  

 <span data-ttu-id="4bba8-119">Çözümlenmemiş bir yöntem, tanımlanan ancak uygulanmayan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4bba8-119">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="4bba8-120">Yöntem işaretlenmişse `miForwardRef` ve ya da `mdPinvokeImpl` sıfır olarak ayarlandıysa, bir yöntem numaralandırmaya dahil edilir `miRuntime` .</span><span class="sxs-lookup"><span data-stu-id="4bba8-120">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="4bba8-121">Diğer bir deyişle, çözümlenmemiş bir yöntem, `miForwardRef` yönetilmeyen kodda uygulanmayan, ancak bir çalışma zamanının kendisi tarafından dahili olarak uygulanan bir sınıf yöntemidir</span><span class="sxs-lookup"><span data-stu-id="4bba8-121">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="4bba8-122">Sabit listesi, modül kapsamında (genel) veya arabirimlerde ya da soyut sınıflarda tanımlanmış tüm yöntemleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="4bba8-122">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bba8-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bba8-123">Requirements</span></span>  

 <span data-ttu-id="4bba8-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bba8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bba8-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4bba8-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bba8-126">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4bba8-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4bba8-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bba8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bba8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bba8-128">See also</span></span>

- [<span data-ttu-id="4bba8-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bba8-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4bba8-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bba8-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
