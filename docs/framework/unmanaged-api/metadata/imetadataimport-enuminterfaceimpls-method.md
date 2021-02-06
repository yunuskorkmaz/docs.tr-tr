---
description: ': IMetaDataImport:: EnumInterfaceImpls Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5276d1edb3be0cae76b18a06241dc6b9952e1a72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649422"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="d8bea-103">IMetaDataImport::EnumInterfaceImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8bea-103">IMetaDataImport::EnumInterfaceImpls Method</span></span>

<span data-ttu-id="d8bea-104">Belirtilen tarafından uygulanan tüm arabirimleri numaralandırır `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="d8bea-104">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d8bea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8bea-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8bea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8bea-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="d8bea-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8bea-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="d8bea-108">'ndaki MethodDef belirteçleri arabirim uygulamalarını temsil eden TypeDef 'in belirteci NUMARALANDIRILAMAZ.</span><span class="sxs-lookup"><span data-stu-id="d8bea-108">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="d8bea-109">dışı MethodDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="d8bea-109">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d8bea-110">'ndaki Dizinin uzunluk üst sınırı `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="d8bea-110">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="d8bea-111">dışı İçinde döndürülen gerçek belirteç sayısı `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="d8bea-111">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8bea-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8bea-112">Return Value</span></span>  
  
|<span data-ttu-id="d8bea-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8bea-113">HRESULT</span></span>|<span data-ttu-id="d8bea-114">Description</span><span class="sxs-lookup"><span data-stu-id="d8bea-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d8bea-115">`EnumInterfaceImpls` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d8bea-115">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d8bea-116">Numaralandırılacak bir MethodDef belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="d8bea-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="d8bea-117">Bu durumda, `pcImpls` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d8bea-117">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="d8bea-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8bea-118">Remarks</span></span>

<span data-ttu-id="d8bea-119">Sabit listesi, `mdInterfaceImpl` belirtilen tarafından uygulanan her arabirim için bir belirteç koleksiyonu döndürür `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="d8bea-119">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="d8bea-120">Arabirim belirteçleri, arabirimlerin belirtildiği sırada döndürülür ( `DefineTypeDef` veya üzerinden `SetTypeDefProps` ).</span><span class="sxs-lookup"><span data-stu-id="d8bea-120">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="d8bea-121">Döndürülen `mdInterfaceImpl` belirteçlerin özellikleri, [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)kullanılarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8bea-121">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d8bea-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8bea-122">Requirements</span></span>  

 <span data-ttu-id="d8bea-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8bea-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8bea-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d8bea-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8bea-125">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d8bea-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8bea-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8bea-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bea-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8bea-127">See also</span></span>

- [<span data-ttu-id="d8bea-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8bea-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d8bea-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8bea-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
