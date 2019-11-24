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
ms.openlocfilehash: 4c819bff50e6644a733374e9863d670d3323ee68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449528"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="9dc27-102">IMetaDataImport::EnumInterfaceImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dc27-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="9dc27-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="9dc27-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="9dc27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dc27-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dc27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9dc27-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9dc27-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="9dc27-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="9dc27-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="9dc27-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="9dc27-108">[out] The array used to store the MethodDef tokens.</span><span class="sxs-lookup"><span data-stu-id="9dc27-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9dc27-109">[in] The maximum size of the `rImpls` array.</span><span class="sxs-lookup"><span data-stu-id="9dc27-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="9dc27-110">[out] The actual number of tokens returned in `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="9dc27-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dc27-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9dc27-111">Return Value</span></span>  
  
|<span data-ttu-id="9dc27-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9dc27-112">HRESULT</span></span>|<span data-ttu-id="9dc27-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dc27-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9dc27-114">`EnumInterfaceImpls` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="9dc27-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9dc27-115">There are no MethodDef tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="9dc27-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="9dc27-116">In that case, `pcImpls` is set to zero.</span><span class="sxs-lookup"><span data-stu-id="9dc27-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="9dc27-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dc27-117">Remarks</span></span>

<span data-ttu-id="9dc27-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="9dc27-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="9dc27-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="9dc27-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="9dc27-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="9dc27-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="9dc27-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dc27-121">Requirements</span></span>  
 <span data-ttu-id="9dc27-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc27-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc27-123">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9dc27-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9dc27-124">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9dc27-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9dc27-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc27-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc27-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dc27-126">See also</span></span>

- [<span data-ttu-id="9dc27-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dc27-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9dc27-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dc27-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
