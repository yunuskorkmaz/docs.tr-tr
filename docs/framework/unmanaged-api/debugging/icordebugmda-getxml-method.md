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
ms.openlocfilehash: cd1882bdfca1258889514a041726a59435e126b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793213"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="826c2-102">ICorDebugMDA::GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="826c2-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="826c2-103">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ILIŞKILI tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="826c2-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="826c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="826c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="826c2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="826c2-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="826c2-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="826c2-107">dışı XML akışının uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="826c2-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="826c2-108">dışı XML akışının depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="826c2-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="826c2-109">Dizi boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="826c2-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="826c2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="826c2-110">Remarks</span></span>  
 <span data-ttu-id="826c2-111">`GetXML` yöntemi, ilişkili XML akışının boyutuna bağlı olarak performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="826c2-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="826c2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="826c2-112">Requirements</span></span>  
 <span data-ttu-id="826c2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="826c2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="826c2-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="826c2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="826c2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="826c2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="826c2-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="826c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826c2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="826c2-117">See also</span></span>

- [<span data-ttu-id="826c2-118">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="826c2-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="826c2-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="826c2-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
