---
title: ICorDebugMDA::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dfe2bb234631a733248066e8475c135de288e63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737604"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="ca435-102">ICorDebugMDA::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="ca435-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="ca435-103">Tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) adını içeren bir dize alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ca435-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca435-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca435-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca435-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca435-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ca435-106">[in] Boyutu `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="ca435-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ca435-107">[out] Bir işaretçi adı uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ca435-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ca435-108">[out] Dizi adı depolanacağı.</span><span class="sxs-lookup"><span data-stu-id="ca435-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca435-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca435-109">Remarks</span></span>  
 <span data-ttu-id="ca435-110">MDA adlarının benzersiz değerler.</span><span class="sxs-lookup"><span data-stu-id="ca435-110">MDA names are unique values.</span></span> <span data-ttu-id="ca435-111">`GetName` XML akışı alma ve ad şemasını temel alan akıştan ayıklanıyor bir uygun performans alternatif bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ca435-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca435-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca435-112">Requirements</span></span>  
 <span data-ttu-id="ca435-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca435-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca435-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca435-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca435-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca435-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca435-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca435-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca435-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca435-117">See also</span></span>
- [<span data-ttu-id="ca435-118">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca435-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="ca435-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="ca435-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
