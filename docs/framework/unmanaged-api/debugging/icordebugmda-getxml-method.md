---
description: ': ICorDebugMDA:: GetXML yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugMDA::GetXML Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: fa506e6e8f306271f10a7a715af9b8bc6a80c1d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801143"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="a4613-103">ICorDebugMDA::GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4613-103">ICorDebugMDA::GetXML Method</span></span>

<span data-ttu-id="a4613-104">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ILIŞKILI tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="a4613-104">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4613-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4613-105">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4613-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4613-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="a4613-107">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a4613-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a4613-108">dışı XML akışının uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4613-108">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="a4613-109">dışı XML akışının depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="a4613-109">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="a4613-110">Dizi boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4613-110">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4613-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4613-111">Remarks</span></span>  

 <span data-ttu-id="a4613-112">`GetXML`Yöntemi, ILIŞKILI XML akışının boyutuna bağlı olarak performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="a4613-112">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4613-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4613-113">Requirements</span></span>  

 <span data-ttu-id="a4613-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4613-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4613-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4613-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4613-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a4613-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4613-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4613-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4613-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4613-118">See also</span></span>

- [<span data-ttu-id="a4613-119">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4613-119">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="a4613-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a4613-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
