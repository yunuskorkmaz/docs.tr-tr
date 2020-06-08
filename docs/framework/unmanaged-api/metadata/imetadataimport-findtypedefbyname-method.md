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
ms.openlocfilehash: 5485f43afe08fafa559d0418327a8f4f186860e7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491517"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="53e47-102">IMetaDataImport::FindTypeDefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53e47-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="53e47-103">Belirtilen ada sahip için TypeDef meta veri belirtecine yönelik bir işaretçi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="53e47-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e47-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="53e47-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53e47-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53e47-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="53e47-106">'ndaki TypeDef belirtecinin alınacağı türün adı.</span><span class="sxs-lookup"><span data-stu-id="53e47-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="53e47-107">'ndaki Kapsayan sınıfı temsil eden bir TypeDef veya TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="53e47-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="53e47-108">Bulunacak tür iç içe bir sınıf değilse, bu değeri NULL olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="53e47-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="53e47-109">dışı Eşleşen TypeDef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="53e47-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e47-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53e47-110">Requirements</span></span>  
 <span data-ttu-id="53e47-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e47-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e47-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="53e47-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53e47-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="53e47-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53e47-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e47-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e47-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53e47-115">See also</span></span>

- [<span data-ttu-id="53e47-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53e47-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="53e47-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53e47-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
