---
title: ICorDebugILFrame2::EnumerateTypeParameters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7454b551edc546fecbd9d091f7c821e0a07b16df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988553"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="482c9-102">ICorDebugILFrame2::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="482c9-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="482c9-103">Icordebugtypeenum nesneyi içeren alır <xref:System.Type> bu çerçeve parametreleri.</span><span class="sxs-lookup"><span data-stu-id="482c9-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="482c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="482c9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="482c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="482c9-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="482c9-106">Numaralandırma tür parametrelerinin izin veren bir Icordebugtypeenum arabirimi nesnesi adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="482c9-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="482c9-107">Tür parametreleri listesi tarafından yöntemi tür parametreleri (varsa) ve ardından sınıf türündeki parametrelere (varsa) içerir.</span><span class="sxs-lookup"><span data-stu-id="482c9-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="482c9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="482c9-108">Remarks</span></span>  
 <span data-ttu-id="482c9-109">Kullanım [Imetadataımport2::enumgenericparams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) kaç sınıf türündeki parametrelere ve yöntem parametreleri içeren bu liste türünü belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="482c9-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="482c9-110">Tür parametreleri her zaman kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="482c9-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="482c9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="482c9-111">Requirements</span></span>  
 <span data-ttu-id="482c9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="482c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="482c9-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="482c9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="482c9-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="482c9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="482c9-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="482c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
