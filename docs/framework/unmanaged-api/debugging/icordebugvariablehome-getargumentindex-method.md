---
title: ICorDebugVariableHome::GetArgumentIndex yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20f65218928ee07d67ea742154469ac3cbea9241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421771"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="76a12-102">ICorDebugVariableHome::GetArgumentIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="76a12-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="76a12-103">Bir işlev bağımsız değişkeni dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="76a12-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76a12-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76a12-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76a12-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="76a12-106">[out] Bağımsız değişken dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="76a12-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76a12-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="76a12-107">Return Value</span></span>  
 <span data-ttu-id="76a12-108">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="76a12-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="76a12-109">Değer</span><span class="sxs-lookup"><span data-stu-id="76a12-109">Value</span></span>|<span data-ttu-id="76a12-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76a12-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="76a12-111">Yöntem çağrısının geçerli bir bağımsız değişken dizin döndürdü.</span><span class="sxs-lookup"><span data-stu-id="76a12-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="76a12-112">Geçerli [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği yerel bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="76a12-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76a12-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76a12-113">Remarks</span></span>  
 <span data-ttu-id="76a12-114">Bağımsız değişken dizini, bu bağımsız değişken için meta verilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76a12-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76a12-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76a12-115">Requirements</span></span>  
 <span data-ttu-id="76a12-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76a12-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76a12-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76a12-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76a12-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76a12-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76a12-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76a12-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a12-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76a12-120">See Also</span></span>  
 [<span data-ttu-id="76a12-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76a12-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
