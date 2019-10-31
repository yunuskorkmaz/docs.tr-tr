---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: b108c8c87d3afdbfacb569ab501274e5c45c2e2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129183"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="95df3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95df3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="95df3-103">Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="95df3-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="95df3-104">Oluşturulan catch 'in Il kayması, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95df3-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="95df3-105">Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95df3-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95df3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95df3-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95df3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95df3-107">Parameters</span></span>  
  
|<span data-ttu-id="95df3-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="95df3-108">Parameter</span></span>|<span data-ttu-id="95df3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95df3-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="95df3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="95df3-110">Return Value</span></span>  
 <span data-ttu-id="95df3-111">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="95df3-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95df3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95df3-112">Requirements</span></span>  
 <span data-ttu-id="95df3-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="95df3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95df3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95df3-114">See also</span></span>

- [<span data-ttu-id="95df3-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95df3-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
