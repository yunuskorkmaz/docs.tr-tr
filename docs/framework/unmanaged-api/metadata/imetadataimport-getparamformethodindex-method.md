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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c6f06ff4fc7d855ea07f1f572a2b7ea948efc51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207064"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="ff68f-102">IMetaDataImport::GetParamForMethodIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff68f-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="ff68f-103">Belirtilen parametre tarafından belirtilen MethodDef belirteç temsil yöntemi temsil eden bir belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="ff68f-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff68f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff68f-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff68f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff68f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="ff68f-106">[in] Parametre belirtecini için döndürülecek yöntemi temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="ff68f-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="ff68f-107">[in] İstenen parametre oluştuğu sıralı konumu parametre listesinde.</span><span class="sxs-lookup"><span data-stu-id="ff68f-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="ff68f-108">Parametreleri bir, sıfır konumda yöntemin dönüş değeri ile başlayarak numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="ff68f-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="ff68f-109">[out] İstenen parametre temsil eden bir ParamDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff68f-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff68f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff68f-110">Requirements</span></span>  
 <span data-ttu-id="ff68f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff68f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff68f-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ff68f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff68f-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ff68f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff68f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff68f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff68f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff68f-115">See also</span></span>

- [<span data-ttu-id="ff68f-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff68f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ff68f-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff68f-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
