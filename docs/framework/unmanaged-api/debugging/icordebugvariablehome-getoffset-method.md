---
description: ': Icordebugvariablehome:: GetOffset Yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugvariablehome:: GetOffset Yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 48b57856d2825dd2ea9328064a28783b4b36029b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728775"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="d3f0c-103">Icordebugvariablehome:: GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3f0c-103">ICorDebugVariableHome::GetOffset Method</span></span>

<span data-ttu-id="d3f0c-104">Bir değişken için temel kaydın konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="d3f0c-104">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f0c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3f0c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3f0c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3f0c-106">Parameters</span></span>  

 `pOffset`  
 <span data-ttu-id="d3f0c-107">dışı Temel kayıttaki fark.</span><span class="sxs-lookup"><span data-stu-id="d3f0c-107">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3f0c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d3f0c-108">Return Value</span></span>  

 <span data-ttu-id="d3f0c-109">Yöntemi aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="d3f0c-109">The method returns the following values:</span></span>  
  
|<span data-ttu-id="d3f0c-110">Değer</span><span class="sxs-lookup"><span data-stu-id="d3f0c-110">Value</span></span>|<span data-ttu-id="d3f0c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3f0c-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d3f0c-112">Değişken, YAZMAÇ göreli bir bellek konumudur.</span><span class="sxs-lookup"><span data-stu-id="d3f0c-112">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d3f0c-113">Değişken, YAZMAÇ göreli bir bellek konumunda değil.</span><span class="sxs-lookup"><span data-stu-id="d3f0c-113">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3f0c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3f0c-114">Requirements</span></span>  

 <span data-ttu-id="d3f0c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f0c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f0c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3f0c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3f0c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3f0c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3f0c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f0c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f0c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3f0c-119">See also</span></span>

- [<span data-ttu-id="d3f0c-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3f0c-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
