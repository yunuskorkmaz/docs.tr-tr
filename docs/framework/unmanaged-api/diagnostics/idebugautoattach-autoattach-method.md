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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e04a447c8562ff797ac98885bded150a3a167136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775788"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="b99c0-102">IDebugAutoAttach::AutoAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b99c0-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="b99c0-103">Hata ayıklayıcı sunucu çağrılan otomatik gerçekleştirir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b99c0-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b99c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b99c0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b99c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b99c0-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="b99c0-106">[in] Her zaman `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="b99c0-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="b99c0-107">[in] İşlem kimliği, normalde alınan `GetCurrentProcessId` işlevi.</span><span class="sxs-lookup"><span data-stu-id="b99c0-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="b99c0-108">[in] Program türü: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, veya `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="b99c0-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="b99c0-109">[in] Program Kimliği</span><span class="sxs-lookup"><span data-stu-id="b99c0-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="b99c0-110">[in] Debug fiilini tarafından geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="b99c0-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b99c0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b99c0-111">Return Value</span></span>  
 <span data-ttu-id="b99c0-112">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="b99c0-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b99c0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b99c0-113">Requirements</span></span>  
 <span data-ttu-id="b99c0-114">**Üst bilgi:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="b99c0-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99c0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b99c0-115">See also</span></span>

- [<span data-ttu-id="b99c0-116">IDebugAutoAttach Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b99c0-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
