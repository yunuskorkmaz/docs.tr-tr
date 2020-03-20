---
title: ICorDebugILFrame::EnumerateLocalVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178838"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="d2104-102">ICorDebugILFrame::EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2104-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="d2104-103">Bu çerçevedeki yerel değişkenler için bir sayısallaştırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d2104-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2104-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2104-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2104-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2104-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="d2104-106">[çıkış] Bu çerçevedeki yerel değişkenlerin sayıcısı olan bir ICorDebugValueEnum nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2104-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2104-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2104-107">Remarks</span></span>  
 <span data-ttu-id="d2104-108">`EnumerateLocalVariables`bu ICorDebugILFrame nesnesi tarafından temsil edilen çağrı çerçevesinde bulunan yerel değişkenleri listeleyen bir enumerator alır.</span><span class="sxs-lookup"><span data-stu-id="d2104-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="d2104-109">Bazıları etkin olmadığından, liste çalışan işlevdeki tüm yerel değişkenleri içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="d2104-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2104-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2104-110">Requirements</span></span>  
 <span data-ttu-id="d2104-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2104-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2104-112">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2104-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2104-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2104-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2104-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2104-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
