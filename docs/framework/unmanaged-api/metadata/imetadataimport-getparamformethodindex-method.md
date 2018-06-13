---
title: IMetaDataImport::GetParamForMethodIndex Metodu
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
ms.openlocfilehash: 31096f7a5fd23bbd54f2beb9258c9d529e94f373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448768"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="23e8d-102">IMetaDataImport::GetParamForMethodIndex Metodu</span><span class="sxs-lookup"><span data-stu-id="23e8d-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="23e8d-103">Belirtilen parametre tarafından belirtilen MethodDef belirteci temsil yöntemi temsil eden belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="23e8d-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23e8d-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23e8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23e8d-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="23e8d-106">[in] İçin parametre belirteci döndürmek için yöntemini temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="23e8d-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="23e8d-107">[in] İstenen parametre oluştuğu sıralı konumu parametre listesi.</span><span class="sxs-lookup"><span data-stu-id="23e8d-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="23e8d-108">Parametreleri birinden yöntemin dönüş değeri sıfır konumda ile başlayarak numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="23e8d-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="23e8d-109">[out] İstenen parametre temsil eden bir ParamDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="23e8d-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23e8d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23e8d-110">Requirements</span></span>  
 <span data-ttu-id="23e8d-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23e8d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23e8d-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23e8d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23e8d-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="23e8d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23e8d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23e8d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e8d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23e8d-115">See Also</span></span>  
 [<span data-ttu-id="23e8d-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23e8d-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="23e8d-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23e8d-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
