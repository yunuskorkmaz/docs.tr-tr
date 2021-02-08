---
description: ': IMetaDataImport:: IsValidToken yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::IsValidToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 68589496213c93f81cfbd0992f9b210e03d6f178
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789066"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="d1aa5-103">IMetaDataImport::IsValidToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1aa5-103">IMetaDataImport::IsValidToken Method</span></span>

<span data-ttu-id="d1aa5-104">Belirtilen belirtecin bir kod nesnesine geçerli bir başvuru içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d1aa5-104">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1aa5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1aa5-105">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1aa5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1aa5-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="d1aa5-107">'ndaki Başvuru geçerliliğini denetlenecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="d1aa5-107">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1aa5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1aa5-108">Return Value</span></span>  

 <span data-ttu-id="d1aa5-109">`true``tk`geçerli kapsam içinde geçerli bir meta veri belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="d1aa5-109">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="d1aa5-110">Tersi durumda `false`.</span><span class="sxs-lookup"><span data-stu-id="d1aa5-110">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1aa5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1aa5-111">Requirements</span></span>  

 <span data-ttu-id="d1aa5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1aa5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1aa5-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1aa5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1aa5-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d1aa5-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1aa5-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1aa5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1aa5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1aa5-116">See also</span></span>

- [<span data-ttu-id="d1aa5-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1aa5-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d1aa5-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1aa5-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
