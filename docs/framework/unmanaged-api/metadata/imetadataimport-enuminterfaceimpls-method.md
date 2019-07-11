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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d0f94949cdc82cdecd52f003f3400c43014fabf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780458"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="49538-102">IMetaDataImport::EnumInterfaceImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49538-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="49538-103">Tüm arabirimleri tarafından belirtilen uygulanan numaralandırır `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="49538-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="49538-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49538-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49538-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49538-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="49538-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49538-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="49538-107">[in] Arabirim uygulamaları gösteren, MethodDef sıralanması belirteçleridir TypeDef belirteç.</span><span class="sxs-lookup"><span data-stu-id="49538-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="49538-108">[out] Dizi MethodDef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49538-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="49538-109">[in] En büyük boyutunu `rImpls` dizisi.</span><span class="sxs-lookup"><span data-stu-id="49538-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="49538-110">[out] Döndürülen belirteç gerçek sayısını `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="49538-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49538-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="49538-111">Return Value</span></span>  
  
|<span data-ttu-id="49538-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49538-112">HRESULT</span></span>|<span data-ttu-id="49538-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49538-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="49538-114">`EnumInterfaceImpls` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="49538-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="49538-115">Numaralandırılacak hiçbir MethodDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="49538-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="49538-116">Bu durumda, `pcImpls` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="49538-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="49538-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49538-117">Remarks</span></span>

<span data-ttu-id="49538-118">Sabit bir koleksiyonunu döndürür `mdInterfaceImpl` belirteçler tarafından belirtilen uygulanan her arabirim için `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="49538-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="49538-119">Arabirimi belirteçleri, arabirimler belirtilmiş sırayla döndürülür (aracılığıyla `DefineTypeDef` veya `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="49538-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="49538-120">Özellikler döndürülen `mdInterfaceImpl` belirteçleri kullanılarak sorgulanabilir [Getınterfaceımplprops](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="49538-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="49538-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49538-121">Requirements</span></span>  
 <span data-ttu-id="49538-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49538-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49538-123">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="49538-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49538-124">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="49538-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49538-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49538-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49538-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49538-126">See also</span></span>

- [<span data-ttu-id="49538-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49538-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="49538-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49538-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
