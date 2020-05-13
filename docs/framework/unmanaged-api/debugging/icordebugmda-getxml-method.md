---
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
ms.openlocfilehash: 219aa27296dffa525bf3e2b836825437a8ce77b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207650"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="2e072-102">ICorDebugMDA::GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e072-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="2e072-103">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ILIŞKILI tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="2e072-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e072-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e072-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e072-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e072-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2e072-106">'ndaki `szName`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="2e072-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2e072-107">dışı XML akışının uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2e072-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="2e072-108">dışı XML akışının depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="2e072-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="2e072-109">Dizi boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e072-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e072-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e072-110">Remarks</span></span>  
 <span data-ttu-id="2e072-111">`GetXML`Yöntemi, ILIŞKILI XML akışının boyutuna bağlı olarak performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="2e072-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e072-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e072-112">Requirements</span></span>  
 <span data-ttu-id="2e072-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e072-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e072-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e072-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e072-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e072-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e072-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e072-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e072-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e072-117">See also</span></span>

- [<span data-ttu-id="2e072-118">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e072-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="2e072-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="2e072-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
