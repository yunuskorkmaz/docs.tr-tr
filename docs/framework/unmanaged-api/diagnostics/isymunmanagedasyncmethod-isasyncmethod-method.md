---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 460d6781405b6042262d50e1aa79ee8c77f781a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489733"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="3486b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3486b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="3486b-103">Yöntemi zaman uyumsuz bilgi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="3486b-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="3486b-104">Bu yöntem döndürürse `FALSE` sonra bu arabirimde diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="3486b-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="3486b-105">Tüm dönüş göründükleri `E_UNEXPECTED` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="3486b-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3486b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3486b-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3486b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3486b-107">Parameters</span></span>  
  
|<span data-ttu-id="3486b-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="3486b-108">Parameter</span></span>|<span data-ttu-id="3486b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3486b-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="3486b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3486b-110">Return Value</span></span>  
 <span data-ttu-id="3486b-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="3486b-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3486b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3486b-112">Requirements</span></span>  
 <span data-ttu-id="3486b-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3486b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3486b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3486b-114">See also</span></span>
- [<span data-ttu-id="3486b-115">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3486b-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
