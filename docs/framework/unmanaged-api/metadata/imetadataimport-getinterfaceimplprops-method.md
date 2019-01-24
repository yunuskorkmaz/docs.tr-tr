---
title: IMetaDataImport::GetInterfaceImplProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91cb42a5bf1115de82b5fe28693cb77b66915c9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600564"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="d23f7-102">IMetaDataImport::GetInterfaceImplProps Metodu</span><span class="sxs-lookup"><span data-stu-id="d23f7-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="d23f7-103">Meta veri belirteçleri için bir işaretçi alır <xref:System.Type> belirtilen yöntemini uygulayan ve arabirim için bu yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="d23f7-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d23f7-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d23f7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d23f7-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="d23f7-106">[in] Sınıf ve arabirim belirteçleri için döndürülecek yöntemi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d23f7-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d23f7-107">[out] Yöntemini uygulayan bir sınıfı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d23f7-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="d23f7-108">[out] Uygulanan yöntemi tanımlar arabirimi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d23f7-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23f7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d23f7-109">Requirements</span></span>  
 <span data-ttu-id="d23f7-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d23f7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23f7-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d23f7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d23f7-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d23f7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d23f7-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23f7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23f7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d23f7-114">See also</span></span>
- [<span data-ttu-id="d23f7-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d23f7-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d23f7-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d23f7-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
