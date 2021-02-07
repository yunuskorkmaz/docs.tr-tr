---
description: ': IMetaDataImport:: GetNestedClassProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5fd812bf9b7725d520b14284db400bb50e82c25b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677545"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="edb9a-103">IMetaDataImport::GetNestedClassProps Metodu</span><span class="sxs-lookup"><span data-stu-id="edb9a-103">IMetaDataImport::GetNestedClassProps Method</span></span>

<span data-ttu-id="edb9a-104">Belirtilen iç içe türün üst öğesi için TypeDef belirtecini alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="edb9a-104">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb9a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edb9a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edb9a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edb9a-106">Parameters</span></span>  

 `tdNestedClass`  
 <span data-ttu-id="edb9a-107">'ndaki <xref:System.Type> İçin üst sınıf belirtecini döndürmek üzere öğesini temsil eden bir typedef belirteci.</span><span class="sxs-lookup"><span data-stu-id="edb9a-107">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="edb9a-108">dışı <xref:System.Type> İçinde iç içe olan Için typedef belirtecine yönelik bir işaretçi `tdNestedClass` .</span><span class="sxs-lookup"><span data-stu-id="edb9a-108">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edb9a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edb9a-109">Requirements</span></span>  

 <span data-ttu-id="edb9a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edb9a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edb9a-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="edb9a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edb9a-112">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="edb9a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="edb9a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edb9a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb9a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb9a-114">See also</span></span>

- [<span data-ttu-id="edb9a-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edb9a-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="edb9a-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edb9a-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
