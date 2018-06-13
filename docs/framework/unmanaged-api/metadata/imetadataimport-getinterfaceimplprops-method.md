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
ms.openlocfilehash: 9fca044b5dce260a1eed55b01531e7ae21a16ebd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446170"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="81c64-102">IMetaDataImport::GetInterfaceImplProps Metodu</span><span class="sxs-lookup"><span data-stu-id="81c64-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="81c64-103">Bir işaretçi için meta veri belirteçlerini alır <xref:System.Type> belirtilen yöntem uygulayan ve arabirim için bu yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="81c64-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c64-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81c64-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81c64-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81c64-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="81c64-106">[in] İçin sınıf ve arabirim belirteçleri döndürmek için yöntemini temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="81c64-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="81c64-107">[out] Yöntem uygulayan sınıfa temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="81c64-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="81c64-108">[out] Uygulanan yöntemi tanımlar arabirimi temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="81c64-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c64-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81c64-109">Requirements</span></span>  
 <span data-ttu-id="81c64-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81c64-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c64-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="81c64-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81c64-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="81c64-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81c64-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c64-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c64-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81c64-114">See Also</span></span>  
 [<span data-ttu-id="81c64-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81c64-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="81c64-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81c64-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
