---
description: ': IMetaDataImport:: GetParamForMethodIndex yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d84b26f1239e548b6cf96d1e6b38791eb6ecddff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728164"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="d7939-103">IMetaDataImport::GetParamForMethodIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7939-103">IMetaDataImport::GetParamForMethodIndex Method</span></span>

<span data-ttu-id="d7939-104">Belirtilen MethodDef belirteci tarafından temsil edilen metodun belirtilen bir parametresini temsil eden belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="d7939-104">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7939-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7939-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7939-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7939-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="d7939-107">'ndaki İçin parametre belirtecini döndürecek yöntemi temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="d7939-107">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d7939-108">'ndaki İstenen parametrenin gerçekleştiği parametre listesindeki sıra konumu.</span><span class="sxs-lookup"><span data-stu-id="d7939-108">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="d7939-109">Parametreler, bir öğesinden başlayarak, yöntemin sıfır konumundaki dönüş değeri ile numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="d7939-109">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="d7939-110">dışı İstenen parametreyi temsil eden bir ParamDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d7939-110">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7939-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7939-111">Requirements</span></span>  

 <span data-ttu-id="d7939-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7939-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7939-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d7939-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7939-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d7939-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d7939-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7939-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7939-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7939-116">See also</span></span>

- [<span data-ttu-id="d7939-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7939-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d7939-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7939-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
