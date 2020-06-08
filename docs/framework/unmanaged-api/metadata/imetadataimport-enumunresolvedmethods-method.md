---
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
ms.openlocfilehash: c991c0af845bc6825db6b3bf258fe0809d5db804
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503706"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="6bf06-102">IMetaDataImport::EnumUnresolvedMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bf06-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="6bf06-103">Geçerli meta veri kapsamındaki çözümlenmemiş yöntemleri temsil eden MemberDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="6bf06-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bf06-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6bf06-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bf06-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bf06-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6bf06-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6bf06-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6bf06-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6bf06-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="6bf06-108">dışı MemberDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="6bf06-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6bf06-109">'ndaki Dizinin en büyük boyutu `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="6bf06-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6bf06-110">dışı İçinde döndürülen MemberDef belirteçleri sayısı `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="6bf06-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bf06-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6bf06-111">Return Value</span></span>  
  
|<span data-ttu-id="6bf06-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bf06-112">HRESULT</span></span>|<span data-ttu-id="6bf06-113">Description</span><span class="sxs-lookup"><span data-stu-id="6bf06-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6bf06-114">`EnumUnresolvedMethods`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6bf06-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6bf06-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="6bf06-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6bf06-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="6bf06-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bf06-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bf06-117">Remarks</span></span>  
 <span data-ttu-id="6bf06-118">Çözümlenmemiş bir yöntem, tanımlanan ancak uygulanmayan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="6bf06-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="6bf06-119">Yöntem işaretlenmişse `miForwardRef` ve ya da `mdPinvokeImpl` sıfır olarak ayarlandıysa, bir yöntem numaralandırmaya dahil edilir `miRuntime` .</span><span class="sxs-lookup"><span data-stu-id="6bf06-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="6bf06-120">Diğer bir deyişle, çözümlenmemiş bir yöntem, `miForwardRef` yönetilmeyen kodda uygulanmayan, ancak bir çalışma zamanının kendisi tarafından dahili olarak uygulanan bir sınıf yöntemidir</span><span class="sxs-lookup"><span data-stu-id="6bf06-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="6bf06-121">Sabit listesi, modül kapsamında (genel) veya arabirimlerde ya da soyut sınıflarda tanımlanmış tüm yöntemleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="6bf06-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bf06-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bf06-122">Requirements</span></span>  
 <span data-ttu-id="6bf06-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bf06-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bf06-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6bf06-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6bf06-125">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6bf06-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bf06-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bf06-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf06-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bf06-127">See also</span></span>

- [<span data-ttu-id="6bf06-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bf06-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6bf06-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bf06-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
