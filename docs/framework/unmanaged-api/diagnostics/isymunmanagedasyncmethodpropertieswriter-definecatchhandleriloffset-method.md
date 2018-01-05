---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54cc369b309d1ffe20d0f3e6a2d4ae4e0443c85f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="6a694-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a694-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="6a694-103">Zaman uyumsuz yöntem sarmalar derleyicinin ürettiği catch işleyicisi için uzaklık IL ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6a694-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="6a694-104">Oluşturulan yakalama IL uzaklığı hata ayıklayıcı tarafından bir kullanıcı kodu yönteminde oluşabilecek olsa bile kullanıcı olmayan kod kabul edildiğinde yakalama işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a694-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="6a694-105">Özellikle, bu yanıt olarak kullanıldığı bir **CatchHandlerFound** özel durum olayı.</span><span class="sxs-lookup"><span data-stu-id="6a694-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a694-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a694-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a694-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a694-107">Parameters</span></span>  
  
|<span data-ttu-id="6a694-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="6a694-108">Parameter</span></span>|<span data-ttu-id="6a694-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a694-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="6a694-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a694-110">Return Value</span></span>  
 <span data-ttu-id="6a694-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="6a694-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a694-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a694-112">Requirements</span></span>  
 <span data-ttu-id="6a694-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a694-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a694-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a694-114">See Also</span></span>  
 [<span data-ttu-id="6a694-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a694-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
