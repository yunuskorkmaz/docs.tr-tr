---
title: "ICorDebugILFrame2::EnumerateTypeParameters Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9180ea68dde667ffe0dc8e15b98cb82efaa667ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="a40db-102">ICorDebugILFrame2::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a40db-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="a40db-103">İçeren bir Icordebugtypeenum nesne alır <xref:System.Type> bu çerçevesinde parametreleri.</span><span class="sxs-lookup"><span data-stu-id="a40db-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a40db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a40db-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a40db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a40db-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="a40db-106">Tür parametreleri listesi veren bir Icordebugtypeenum arabirimi nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a40db-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="a40db-107">Tür parametreleri listesini (varsa) ve ardından yöntemi türü parametrelerini sınıfı tür parametreleri (varsa) içerir.</span><span class="sxs-lookup"><span data-stu-id="a40db-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a40db-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a40db-108">Remarks</span></span>  
 <span data-ttu-id="a40db-109">Kullanım [Imetadataımport2::enumgenericparams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) kaç sınıfı tür parametreleri ve yöntemi türü bu listeyi içeren parametreleri belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a40db-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="a40db-110">Tür parametreleri her zaman kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="a40db-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a40db-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a40db-111">Requirements</span></span>  
 <span data-ttu-id="a40db-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a40db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a40db-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a40db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a40db-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a40db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a40db-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a40db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
