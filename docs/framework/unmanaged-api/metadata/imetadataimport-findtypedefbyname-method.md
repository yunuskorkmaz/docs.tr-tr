---
description: ': IMetaDataImport:: FindTypeDefByName yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 083f786cc03b83cda54497937e376baa4a2cbee3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789235"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="1aca3-103">IMetaDataImport::FindTypeDefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aca3-103">IMetaDataImport::FindTypeDefByName Method</span></span>

<span data-ttu-id="1aca3-104">Belirtilen ada sahip için TypeDef meta veri belirtecine yönelik bir işaretçi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="1aca3-104">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aca3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1aca3-105">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aca3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1aca3-106">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="1aca3-107">'ndaki TypeDef belirtecinin alınacağı türün adı.</span><span class="sxs-lookup"><span data-stu-id="1aca3-107">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="1aca3-108">'ndaki Kapsayan sınıfı temsil eden bir TypeDef veya TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="1aca3-108">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="1aca3-109">Bulunacak tür iç içe bir sınıf değilse, bu değeri NULL olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1aca3-109">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="1aca3-110">dışı Eşleşen TypeDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1aca3-110">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aca3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1aca3-111">Requirements</span></span>  

 <span data-ttu-id="1aca3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aca3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aca3-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1aca3-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1aca3-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1aca3-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1aca3-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aca3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aca3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1aca3-116">See also</span></span>

- [<span data-ttu-id="1aca3-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aca3-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1aca3-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aca3-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
