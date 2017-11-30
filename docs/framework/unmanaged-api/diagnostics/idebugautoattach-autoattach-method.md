---
title: "IDebugAutoAttach::AutoAttach Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebugAutoAttach.AutoAttach
api_location: diasymreader.dll
api_type: COM
f1_keywords: IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 359aaf96c42a661657028d508f096f9625d4ba71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="71f49-102">IDebugAutoAttach::AutoAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71f49-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="71f49-103">Hata ayıklayıcı sunucu çağrılan otomatik gerçekleştirir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="71f49-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71f49-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="71f49-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71f49-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="71f49-106">[in] Her zaman `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="71f49-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="71f49-107">[in] İşlem kimliği, normalde ile alınan `GetCurrentProcessId` işlevi.</span><span class="sxs-lookup"><span data-stu-id="71f49-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="71f49-108">[in] Program türü: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, veya `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="71f49-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="71f49-109">[in] Program Kimliği</span><span class="sxs-lookup"><span data-stu-id="71f49-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="71f49-110">[in] Debug fiilini tarafından geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="71f49-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71f49-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="71f49-111">Return Value</span></span>  
 <span data-ttu-id="71f49-112">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="71f49-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f49-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71f49-113">Requirements</span></span>  
 <span data-ttu-id="71f49-114">**Başlık:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="71f49-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f49-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71f49-115">See Also</span></span>  
 [<span data-ttu-id="71f49-116">Idebugautoattach arabirimi</span><span class="sxs-lookup"><span data-stu-id="71f49-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
