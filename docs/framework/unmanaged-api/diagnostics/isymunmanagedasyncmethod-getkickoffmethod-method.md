---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174947"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="0bdb1-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0bdb1-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="0bdb1-103">Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="0bdb1-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bdb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bdb1-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bdb1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0bdb1-105">Parameters</span></span>  
  
|<span data-ttu-id="0bdb1-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="0bdb1-106">Parameter</span></span>|<span data-ttu-id="0bdb1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bdb1-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="0bdb1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0bdb1-108">Return Value</span></span>  
 <span data-ttu-id="0bdb1-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bdb1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0bdb1-110">Requirements</span></span>  
 <span data-ttu-id="0bdb1-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0bdb1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bdb1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-112">See also</span></span>

- [<span data-ttu-id="0bdb1-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0bdb1-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
