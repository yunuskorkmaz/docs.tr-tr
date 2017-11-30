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
ms.openlocfilehash: 3bae0e2dfb56883a674b282acd385ba45a25bebb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="5c9ad-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c9ad-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="5c9ad-103">Zaman uyumsuz yöntem sarmalar derleyicinin ürettiği catch işleyicisi için uzaklık IL ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5c9ad-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="5c9ad-104">Oluşturulan yakalama IL uzaklığı hata ayıklayıcı tarafından bir kullanıcı kodu yönteminde oluşabilecek olsa bile kullanıcı olmayan kod kabul edildiğinde yakalama işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c9ad-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="5c9ad-105">Özellikle, bu yanıt olarak kullanıldığı bir **CatchHandlerFound** özel durum olayı.</span><span class="sxs-lookup"><span data-stu-id="5c9ad-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9ad-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c9ad-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c9ad-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c9ad-107">Parameters</span></span>  
  
|<span data-ttu-id="5c9ad-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="5c9ad-108">Parameter</span></span>|<span data-ttu-id="5c9ad-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c9ad-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="5c9ad-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c9ad-110">Return Value</span></span>  
 <span data-ttu-id="5c9ad-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="5c9ad-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9ad-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c9ad-112">Requirements</span></span>  
 <span data-ttu-id="5c9ad-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5c9ad-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9ad-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c9ad-114">See Also</span></span>  
 [<span data-ttu-id="5c9ad-115">Isymunmanagedasyncmethodpropertieswriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c9ad-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
