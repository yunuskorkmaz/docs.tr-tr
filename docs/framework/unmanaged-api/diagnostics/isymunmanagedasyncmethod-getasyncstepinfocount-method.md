---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 32a4e084-09b2-4946-a4a7-19a1fed9f7cc
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62b6202949432590a87545f3ae243fd828da31ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfocount-method"></a><span data-ttu-id="0ca70-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Metodu</span><span class="sxs-lookup"><span data-stu-id="0ca70-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Method</span></span>
<span data-ttu-id="0ca70-103">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ca70-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ca70-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfoCount(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ca70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ca70-105">Parameters</span></span>  
  
|<span data-ttu-id="0ca70-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="0ca70-106">Parameter</span></span>|<span data-ttu-id="0ca70-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ca70-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="0ca70-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ca70-108">Return Value</span></span>  
 <span data-ttu-id="0ca70-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0ca70-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca70-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ca70-110">Requirements</span></span>  
 <span data-ttu-id="0ca70-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0ca70-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca70-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ca70-112">See Also</span></span>  
 [<span data-ttu-id="0ca70-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ca70-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
