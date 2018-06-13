---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f5bf8252986ffa90ea5380d5342595cb91e5419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424947"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="47d5b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47d5b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="47d5b-103">Metodu zaman uyumsuz bilgi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="47d5b-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="47d5b-104">Bu yöntem döndürürse `FALSE` sonra da bu arabirimi diğer yöntemleri çağırmak için geçersiz.</span><span class="sxs-lookup"><span data-stu-id="47d5b-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="47d5b-105">Tüm iade edecek `E_UNEXPECTED` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="47d5b-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d5b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47d5b-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47d5b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47d5b-107">Parameters</span></span>  
  
|<span data-ttu-id="47d5b-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="47d5b-108">Parameter</span></span>|<span data-ttu-id="47d5b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47d5b-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="47d5b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47d5b-110">Return Value</span></span>  
 <span data-ttu-id="47d5b-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="47d5b-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47d5b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47d5b-112">Requirements</span></span>  
 <span data-ttu-id="47d5b-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47d5b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d5b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47d5b-114">See Also</span></span>  
 [<span data-ttu-id="47d5b-115">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47d5b-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
