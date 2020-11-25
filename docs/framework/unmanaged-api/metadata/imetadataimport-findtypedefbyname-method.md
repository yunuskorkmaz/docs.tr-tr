---
title: IMetaDataImport::FindTypeDefByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: df1516a916b2b48080e4f94937fba063926330ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711305"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="5f67f-102">IMetaDataImport::FindTypeDefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f67f-102">IMetaDataImport::FindTypeDefByName Method</span></span>

<span data-ttu-id="5f67f-103">Belirtilen ada sahip için TypeDef meta veri belirtecine yönelik bir işaretçi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="5f67f-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f67f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5f67f-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f67f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f67f-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="5f67f-106">'ndaki TypeDef belirtecinin alınacağı türün adı.</span><span class="sxs-lookup"><span data-stu-id="5f67f-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="5f67f-107">'ndaki Kapsayan sınıfı temsil eden bir TypeDef veya TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="5f67f-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="5f67f-108">Bulunacak tür iç içe bir sınıf değilse, bu değeri NULL olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5f67f-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5f67f-109">dışı Eşleşen TypeDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5f67f-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f67f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f67f-110">Requirements</span></span>  

 <span data-ttu-id="5f67f-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f67f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f67f-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5f67f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f67f-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5f67f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f67f-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f67f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f67f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f67f-115">See also</span></span>

- [<span data-ttu-id="5f67f-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f67f-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5f67f-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f67f-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
