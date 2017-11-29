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
ms.openlocfilehash: 4d04c34bdc1b61f81fa542dfb22de9a6998f9cc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="8f5e4-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="8f5e4-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="8f5e4-103">Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="8f5e4-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f5e4-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f5e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f5e4-105">Parameters</span></span>  
  
|<span data-ttu-id="8f5e4-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="8f5e4-106">Parameter</span></span>|<span data-ttu-id="8f5e4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f5e4-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="8f5e4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f5e4-108">Return Value</span></span>  
 <span data-ttu-id="8f5e4-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="8f5e4-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f5e4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f5e4-110">Requirements</span></span>  
 <span data-ttu-id="8f5e4-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8f5e4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5e4-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f5e4-112">See Also</span></span>  
 [<span data-ttu-id="8f5e4-113">Isymunmanagedasyncmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f5e4-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
