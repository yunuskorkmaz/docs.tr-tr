---
title: "ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce91552d7468579d9941c1da75c4d281999d66fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="d4b07-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4b07-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="d4b07-103">Metodu zaman uyumsuz bilgi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="d4b07-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="d4b07-104">Bu yöntem döndürürse `FALSE` sonra da bu arabirimi diğer yöntemleri çağırmak için geçersiz.</span><span class="sxs-lookup"><span data-stu-id="d4b07-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="d4b07-105">Tüm iade edecek `E_UNEXPECTED` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="d4b07-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b07-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4b07-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4b07-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4b07-107">Parameters</span></span>  
  
|<span data-ttu-id="d4b07-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="d4b07-108">Parameter</span></span>|<span data-ttu-id="d4b07-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4b07-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="d4b07-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d4b07-110">Return Value</span></span>  
 <span data-ttu-id="d4b07-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d4b07-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b07-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4b07-112">Requirements</span></span>  
 <span data-ttu-id="d4b07-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d4b07-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b07-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4b07-114">See Also</span></span>  
 [<span data-ttu-id="d4b07-115">Isymunmanagedasyncmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4b07-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
