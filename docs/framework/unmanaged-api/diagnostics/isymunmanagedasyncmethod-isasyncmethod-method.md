---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5cddf34f1a6277e966901c9692bff63e26a3b8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136740"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="37080-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37080-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="37080-103">Yöntemi zaman uyumsuz bilgi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="37080-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="37080-104">Bu yöntem döndürürse `FALSE` sonra bu arabirimde diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="37080-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="37080-105">Tüm dönüş göründükleri `E_UNEXPECTED` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="37080-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37080-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37080-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37080-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37080-107">Parameters</span></span>  
  
|<span data-ttu-id="37080-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="37080-108">Parameter</span></span>|<span data-ttu-id="37080-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37080-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="37080-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37080-110">Return Value</span></span>  
 <span data-ttu-id="37080-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="37080-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37080-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37080-112">Requirements</span></span>  
 <span data-ttu-id="37080-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="37080-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37080-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37080-114">See also</span></span>

- [<span data-ttu-id="37080-115">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37080-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
