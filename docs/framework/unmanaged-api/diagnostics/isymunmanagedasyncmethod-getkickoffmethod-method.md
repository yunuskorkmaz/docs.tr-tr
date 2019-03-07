---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84aef2b26e008d1a3c6d95d7ec1e130ab0594a11
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484556"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="27821-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27821-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="27821-103">Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="27821-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27821-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27821-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27821-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27821-105">Parameters</span></span>  
  
|<span data-ttu-id="27821-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="27821-106">Parameter</span></span>|<span data-ttu-id="27821-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27821-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="27821-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="27821-108">Return Value</span></span>  
 <span data-ttu-id="27821-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="27821-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27821-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27821-110">Requirements</span></span>  
 <span data-ttu-id="27821-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27821-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27821-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27821-112">See also</span></span>
- [<span data-ttu-id="27821-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27821-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
