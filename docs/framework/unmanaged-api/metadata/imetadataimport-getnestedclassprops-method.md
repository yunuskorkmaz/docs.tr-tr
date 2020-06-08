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
ms.openlocfilehash: 82cf5e14520f0e677c2d274cf013d8a0020e8fa2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503542"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="c9b85-102">IMetaDataImport::GetNestedClassProps Metodu</span><span class="sxs-lookup"><span data-stu-id="c9b85-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="c9b85-103">Belirtilen iç içe türün üst öğesi için TypeDef belirtecini alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="c9b85-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b85-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c9b85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9b85-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9b85-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="c9b85-106">'ndaki <xref:System.Type>İçin üst sınıf belirtecini döndürmek üzere öğesini temsil eden bir typedef belirteci.</span><span class="sxs-lookup"><span data-stu-id="c9b85-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="c9b85-107">dışı <xref:System.Type>İçinde iç içe olan Için typedef belirtecine yönelik bir işaretçi `tdNestedClass` .</span><span class="sxs-lookup"><span data-stu-id="c9b85-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9b85-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9b85-108">Requirements</span></span>  
 <span data-ttu-id="c9b85-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9b85-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9b85-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c9b85-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9b85-111">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c9b85-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9b85-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9b85-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b85-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9b85-113">See also</span></span>

- [<span data-ttu-id="c9b85-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9b85-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c9b85-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9b85-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
