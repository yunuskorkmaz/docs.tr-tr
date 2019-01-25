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
ms.openlocfilehash: 6b45b5e1a7589329b788160df3ac4493efa48197
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663524"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="4ba7c-102">IDebugAutoAttach::AutoAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ba7c-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="4ba7c-103">Hata ayıklayıcı sunucu çağrılan otomatik gerçekleştirir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ba7c-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ba7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ba7c-104">Syntax</span></span>  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ba7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ba7c-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="4ba7c-106">[in] Her zaman `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="4ba7c-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="4ba7c-107">[in] İşlem kimliği, normalde alınan `GetCurrentProcessId` işlevi.</span><span class="sxs-lookup"><span data-stu-id="4ba7c-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="4ba7c-108">[in] Program türü: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, veya `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="4ba7c-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="4ba7c-109">[in] Program Kimliği</span><span class="sxs-lookup"><span data-stu-id="4ba7c-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="4ba7c-110">[in] Debug fiilini tarafından geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="4ba7c-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ba7c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4ba7c-111">Return Value</span></span>  
 <span data-ttu-id="4ba7c-112">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="4ba7c-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ba7c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ba7c-113">Requirements</span></span>  
 <span data-ttu-id="4ba7c-114">**Üst bilgi:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="4ba7c-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba7c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ba7c-115">See also</span></span>
- [<span data-ttu-id="4ba7c-116">IDebugAutoAttach Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ba7c-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
