---
title: ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96040ee5f56ade3647367c4b879c8aa9e7f460fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="8dec0-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="8dec0-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="8dec0-103">Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="8dec0-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dec0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dec0-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8dec0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dec0-105">Parameters</span></span>  
  
|<span data-ttu-id="8dec0-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="8dec0-106">Parameter</span></span>|<span data-ttu-id="8dec0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dec0-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="8dec0-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8dec0-108">Return Value</span></span>  
 <span data-ttu-id="8dec0-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="8dec0-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dec0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dec0-110">Requirements</span></span>  
 <span data-ttu-id="8dec0-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8dec0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dec0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8dec0-112">See Also</span></span>  
 [<span data-ttu-id="8dec0-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dec0-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
