---
description: ': Idebugoto Attach:: oto Attach yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8abd35b1d94fc074d4dafe424c52c274b1de1541
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800363"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="06549-103">IDebugAutoAttach::AutoAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06549-103">IDebugAutoAttach::AutoAttach Method</span></span>

<span data-ttu-id="06549-104">Sunucu tarafından çağrılan hata ayıklayıcı otomatik iliştirme işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="06549-104">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06549-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06549-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="06549-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06549-106">Parameters</span></span>  

 `guidPort`  
 <span data-ttu-id="06549-107">'ndaki Her zaman olarak ayarlayın `GUID_NULL` .</span><span class="sxs-lookup"><span data-stu-id="06549-107">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="06549-108">'ndaki İşlem KIMLIĞI, normalde `GetCurrentProcessId` işlevle alındı.</span><span class="sxs-lookup"><span data-stu-id="06549-108">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="06549-109">'ndaki Program türü: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` , veya `AUTOATTACH_PROGRAM_UNKNOWN` .</span><span class="sxs-lookup"><span data-stu-id="06549-109">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="06549-110">'ndaki Program KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="06549-110">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="06549-111">'ndaki Hata ayıklama fiili tarafından geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="06549-111">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06549-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06549-112">Return Value</span></span>  

 <span data-ttu-id="06549-113">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="06549-113">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06549-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06549-114">Requirements</span></span>  

 <span data-ttu-id="06549-115">**Üst bilgi:** Dbgoto Attach. h</span><span class="sxs-lookup"><span data-stu-id="06549-115">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06549-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06549-116">See also</span></span>

- [<span data-ttu-id="06549-117">IDebugAutoAttach Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06549-117">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
