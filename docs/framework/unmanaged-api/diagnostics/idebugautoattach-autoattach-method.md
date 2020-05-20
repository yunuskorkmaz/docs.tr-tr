---
title: IDebugAutoAttach::AutoAttach Yöntemi
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442130"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="8792d-102">IDebugAutoAttach::AutoAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8792d-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="8792d-103">Sunucu tarafından çağrılan hata ayıklayıcı otomatik iliştirme işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8792d-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8792d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8792d-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8792d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8792d-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="8792d-106">'ndaki Her zaman olarak ayarlayın `GUID_NULL` .</span><span class="sxs-lookup"><span data-stu-id="8792d-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="8792d-107">'ndaki İşlem KIMLIĞI, normalde `GetCurrentProcessId` işlevle alındı.</span><span class="sxs-lookup"><span data-stu-id="8792d-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="8792d-108">'ndaki Program türü: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` , veya `AUTOATTACH_PROGRAM_UNKNOWN` .</span><span class="sxs-lookup"><span data-stu-id="8792d-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="8792d-109">'ndaki Program KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8792d-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="8792d-110">'ndaki Hata ayıklama fiili tarafından geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="8792d-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8792d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8792d-111">Return Value</span></span>  
 <span data-ttu-id="8792d-112">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="8792d-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8792d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8792d-113">Requirements</span></span>  
 <span data-ttu-id="8792d-114">**Üst bilgi:** Dbgoto Attach. h</span><span class="sxs-lookup"><span data-stu-id="8792d-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8792d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8792d-115">See also</span></span>

- [<span data-ttu-id="8792d-116">IDebugAutoAttach Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8792d-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
