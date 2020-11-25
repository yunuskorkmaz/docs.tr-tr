---
title: IMetaDataImport::EnumInterfaceImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 0b040a2741a44b9d361dabc38c26b8934659003b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711526"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="533b5-102">IMetaDataImport::EnumInterfaceImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="533b5-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>

<span data-ttu-id="533b5-103">Belirtilen tarafından uygulanan tüm arabirimleri numaralandırır `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="533b5-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="533b5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="533b5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="533b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="533b5-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="533b5-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="533b5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="533b5-107">'ndaki MethodDef belirteçleri arabirim uygulamalarını temsil eden TypeDef 'in belirteci NUMARALANDIRILAMAZ.</span><span class="sxs-lookup"><span data-stu-id="533b5-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="533b5-108">dışı MethodDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="533b5-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="533b5-109">'ndaki Dizinin uzunluk üst sınırı `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="533b5-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="533b5-110">dışı İçinde döndürülen gerçek belirteç sayısı `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="533b5-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="533b5-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="533b5-111">Return Value</span></span>  
  
|<span data-ttu-id="533b5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="533b5-112">HRESULT</span></span>|<span data-ttu-id="533b5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="533b5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="533b5-114">`EnumInterfaceImpls` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="533b5-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="533b5-115">Numaralandırılacak bir MethodDef belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="533b5-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="533b5-116">Bu durumda, `pcImpls` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="533b5-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="533b5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="533b5-117">Remarks</span></span>

<span data-ttu-id="533b5-118">Sabit listesi, `mdInterfaceImpl` belirtilen tarafından uygulanan her arabirim için bir belirteç koleksiyonu döndürür `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="533b5-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="533b5-119">Arabirim belirteçleri, arabirimlerin belirtildiği sırada döndürülür ( `DefineTypeDef` veya üzerinden `SetTypeDefProps` ).</span><span class="sxs-lookup"><span data-stu-id="533b5-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="533b5-120">Döndürülen `mdInterfaceImpl` belirteçlerin özellikleri, [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)kullanılarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="533b5-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="533b5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="533b5-121">Requirements</span></span>  

 <span data-ttu-id="533b5-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="533b5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="533b5-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="533b5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="533b5-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="533b5-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="533b5-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="533b5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="533b5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="533b5-126">See also</span></span>

- [<span data-ttu-id="533b5-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="533b5-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="533b5-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="533b5-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
