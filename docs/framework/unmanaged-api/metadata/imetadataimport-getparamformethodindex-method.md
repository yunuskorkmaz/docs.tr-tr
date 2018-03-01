---
title: IMetaDataImport::GetParamForMethodIndex Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0cedc993e6b8794a15ff9927b06ff650ed76b79e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="2f204-102">IMetaDataImport::GetParamForMethodIndex Metodu</span><span class="sxs-lookup"><span data-stu-id="2f204-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="2f204-103">Belirtilen parametre tarafından belirtilen MethodDef belirteci temsil yöntemi temsil eden belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="2f204-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f204-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f204-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f204-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f204-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="2f204-106">[in] İçin parametre belirteci döndürmek için yöntemini temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="2f204-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="2f204-107">[in] İstenen parametre oluştuğu sıralı konumu parametre listesi.</span><span class="sxs-lookup"><span data-stu-id="2f204-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="2f204-108">Parametreleri birinden yöntemin dönüş değeri sıfır konumda ile başlayarak numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="2f204-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="2f204-109">[out] İstenen parametre temsil eden bir ParamDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f204-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f204-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f204-110">Requirements</span></span>  
 <span data-ttu-id="2f204-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f204-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f204-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2f204-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f204-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2f204-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f204-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f204-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f204-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f204-115">See Also</span></span>  
 [<span data-ttu-id="2f204-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f204-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2f204-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f204-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
