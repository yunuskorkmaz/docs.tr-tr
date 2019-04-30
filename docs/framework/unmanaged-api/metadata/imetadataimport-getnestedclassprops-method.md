---
title: IMetaDataImport::GetNestedClassProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb5820087001a207af0c2552f91b4c17f5f78ff7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777663"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="fa5bc-102">IMetaDataImport::GetNestedClassProps Metodu</span><span class="sxs-lookup"><span data-stu-id="fa5bc-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="fa5bc-103">TypeDef üst belirtecini alır <xref:System.Type> türü belirtilen iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="fa5bc-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa5bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa5bc-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa5bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa5bc-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="fa5bc-106">[in] TypeDef belirteci temsil eden bir <xref:System.Type> üst sınıfın döndürülecek belirteci.</span><span class="sxs-lookup"><span data-stu-id="fa5bc-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="fa5bc-107">[out] TypeDef belirteç için bir işaretçiye <xref:System.Type> , `tdNestedClass` iç içe yerleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="fa5bc-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa5bc-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa5bc-108">Requirements</span></span>  
 <span data-ttu-id="fa5bc-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa5bc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa5bc-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fa5bc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa5bc-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fa5bc-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa5bc-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa5bc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa5bc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa5bc-113">See also</span></span>

- [<span data-ttu-id="fa5bc-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa5bc-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fa5bc-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa5bc-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
