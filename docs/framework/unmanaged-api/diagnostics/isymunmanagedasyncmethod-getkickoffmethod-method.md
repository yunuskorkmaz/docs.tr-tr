---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod Metodu
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f20039318d6e1230ccc0fbd203fc44686806bb2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604476"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="843f3-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Metodu</span><span class="sxs-lookup"><span data-stu-id="843f3-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="843f3-103">Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="843f3-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="843f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="843f3-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="843f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="843f3-105">Parameters</span></span>  
  
|<span data-ttu-id="843f3-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="843f3-106">Parameter</span></span>|<span data-ttu-id="843f3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="843f3-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="843f3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="843f3-108">Return Value</span></span>  
 <span data-ttu-id="843f3-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="843f3-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="843f3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="843f3-110">Requirements</span></span>  
 <span data-ttu-id="843f3-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="843f3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="843f3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="843f3-112">See also</span></span>
- [<span data-ttu-id="843f3-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="843f3-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
