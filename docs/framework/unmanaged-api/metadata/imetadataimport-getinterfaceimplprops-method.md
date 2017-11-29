---
title: IMetaDataImport::GetInterfaceImplProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetInterfaceImplProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0843c9823ba40944e6ea075d469f9a76510d8714
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="0f06f-102">IMetaDataImport::GetInterfaceImplProps Metodu</span><span class="sxs-lookup"><span data-stu-id="0f06f-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="0f06f-103">Bir işaretçi için meta veri belirteçlerini alır <xref:System.Type> belirtilen yöntem uygulayan ve arabirim için bu yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="0f06f-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f06f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f06f-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f06f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f06f-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="0f06f-106">[in] İçin sınıf ve arabirim belirteçleri döndürmek için yöntemini temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="0f06f-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="0f06f-107">[out] Yöntem uygulayan sınıfa temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="0f06f-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="0f06f-108">[out] Uygulanan yöntemi tanımlar arabirimi temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="0f06f-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f06f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f06f-109">Requirements</span></span>  
 <span data-ttu-id="0f06f-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f06f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f06f-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0f06f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f06f-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0f06f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f06f-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f06f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f06f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f06f-114">See Also</span></span>  
 [<span data-ttu-id="0f06f-115">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f06f-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0f06f-116">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f06f-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
