---
title: IMetaDataImport::GetNestedClassProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNestedClassProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bbfe382a9a2fdf8ece1015ee73c3d9ef604ec7e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="30692-102">IMetaDataImport::GetNestedClassProps Metodu</span><span class="sxs-lookup"><span data-stu-id="30692-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="30692-103">TypeDef için üst belirtecini alır <xref:System.Type> türü belirtilen iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="30692-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30692-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30692-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30692-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30692-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="30692-106">[in] TypeDef belirteci temsil eden bir <xref:System.Type> üst sınıfın döndürülecek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="30692-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="30692-107">[out] TypeDef belirteci için bir işaretçi <xref:System.Type> , `tdNestedClass` iç içe yerleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="30692-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30692-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30692-108">Requirements</span></span>  
 <span data-ttu-id="30692-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30692-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30692-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="30692-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30692-111">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="30692-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30692-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30692-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30692-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30692-113">See Also</span></span>  
 [<span data-ttu-id="30692-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30692-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="30692-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30692-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
