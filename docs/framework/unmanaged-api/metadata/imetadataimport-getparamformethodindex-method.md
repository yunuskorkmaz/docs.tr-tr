---
title: IMetaDataImport::GetParamForMethodIndex Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
ms.openlocfilehash: d4d3ba5713398876b55c072f0cda7eb5d599c4d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729295"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="e5783-102">IMetaDataImport::GetParamForMethodIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5783-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>

<span data-ttu-id="e5783-103">Belirtilen MethodDef belirteci tarafından temsil edilen metodun belirtilen bir parametresini temsil eden belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="e5783-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5783-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e5783-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5783-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5783-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="e5783-106">'ndaki İçin parametre belirtecini döndürecek yöntemi temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="e5783-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e5783-107">'ndaki İstenen parametrenin gerçekleştiği parametre listesindeki sıra konumu.</span><span class="sxs-lookup"><span data-stu-id="e5783-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="e5783-108">Parametreler, bir öğesinden başlayarak, yöntemin sıfır konumundaki dönüş değeri ile numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="e5783-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="e5783-109">dışı İstenen parametreyi temsil eden bir ParamDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e5783-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5783-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5783-110">Requirements</span></span>  

 <span data-ttu-id="e5783-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5783-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5783-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e5783-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5783-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e5783-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5783-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5783-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5783-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5783-115">See also</span></span>

- [<span data-ttu-id="e5783-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5783-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e5783-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5783-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
