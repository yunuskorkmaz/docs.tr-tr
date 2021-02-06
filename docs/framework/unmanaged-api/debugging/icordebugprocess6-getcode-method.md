---
description: 'Daha fazla bilgi edinin: ICorDebugProcess6:: GetCode yöntemi'
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: a7cb71ddb1e65cda37d762a0fba958d413145138
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649669"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="f480f-103">ICorDebugProcess6::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="f480f-103">ICorDebugProcess6::GetCode Method</span></span>

<span data-ttu-id="f480f-104">Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="f480f-104">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f480f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f480f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f480f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f480f-106">Parameters</span></span>  

 `codeAddress`  
 <span data-ttu-id="f480f-107">'ndaki Yönetilen kod segmentinin başlangıç adresini belirten [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="f480f-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="f480f-108">dışı Yönetilen kod segmentini temsil eden bir "ICorDebugCode" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f480f-108">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f480f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f480f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f480f-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f480f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f480f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f480f-111">Requirements</span></span>  

 <span data-ttu-id="f480f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f480f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f480f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f480f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f480f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f480f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f480f-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f480f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f480f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f480f-116">See also</span></span>

- [<span data-ttu-id="f480f-117">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f480f-117">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="f480f-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f480f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
