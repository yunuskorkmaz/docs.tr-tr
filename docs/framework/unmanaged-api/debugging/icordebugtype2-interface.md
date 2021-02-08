---
description: 'Daha fazla bilgi edinin: ICorDebugType2 Interface'
title: ICorDebugType2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 8691cf294e835bef0f5a0ac694110f73577fb5d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800875"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="3084d-103">ICorDebugType2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3084d-103">ICorDebugType2 Interface</span></span>

<span data-ttu-id="3084d-104">Bir temel türün tür tanımlayıcısını veya karmaşık (Kullanıcı tanımlı) türünü almak için ICorDebugType arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="3084d-104">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3084d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3084d-105">Methods</span></span>  
  
|<span data-ttu-id="3084d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3084d-106">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="3084d-107">GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3084d-107">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="3084d-108">Bu tür için bir [COR_TYPEID](cor-typeid-structure.md) alır.</span><span class="sxs-lookup"><span data-stu-id="3084d-108">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3084d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3084d-109">Remarks</span></span>  

 <span data-ttu-id="3084d-110">Bu arabirim, ICorDebugType arabiriminin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="3084d-110">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3084d-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="3084d-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3084d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3084d-112">Example</span></span>  

 <span data-ttu-id="3084d-113">Aşağıdaki kod parçası, [ICorDebugType2:: GetTypeId](icordebugtype2-gettypeid-method.md) yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3084d-113">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="3084d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3084d-114">Requirements</span></span>  

 <span data-ttu-id="3084d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3084d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3084d-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3084d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3084d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3084d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3084d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3084d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3084d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3084d-119">See also</span></span>

- [<span data-ttu-id="3084d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3084d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
