---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 049f8e4d04498b70533134c01765af2d996d86dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499112"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="8e549-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e549-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="8e549-103">Yöntemi zaman uyumsuz bilgi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="8e549-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="8e549-104">Bu yöntem döndürürse `FALSE` sonra bu arabirimde diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="8e549-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="8e549-105">Tüm dönüş göründükleri `E_UNEXPECTED` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="8e549-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e549-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e549-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e549-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e549-107">Parameters</span></span>  
  
|<span data-ttu-id="8e549-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="8e549-108">Parameter</span></span>|<span data-ttu-id="8e549-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e549-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="8e549-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e549-110">Return Value</span></span>  
 <span data-ttu-id="8e549-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="8e549-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e549-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e549-112">Requirements</span></span>  
 <span data-ttu-id="8e549-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8e549-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e549-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e549-114">See also</span></span>
- [<span data-ttu-id="8e549-115">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e549-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
