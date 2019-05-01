---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940211"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="bbe6e-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbe6e-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="bbe6e-103">Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="bbe6e-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbe6e-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbe6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbe6e-105">Parameters</span></span>  
  
|<span data-ttu-id="bbe6e-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="bbe6e-106">Parameter</span></span>|<span data-ttu-id="bbe6e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbe6e-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="bbe6e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bbe6e-108">Return Value</span></span>  
 <span data-ttu-id="bbe6e-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="bbe6e-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbe6e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbe6e-110">Requirements</span></span>  
 <span data-ttu-id="bbe6e-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bbe6e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe6e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbe6e-112">See also</span></span>

- [<span data-ttu-id="bbe6e-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbe6e-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
