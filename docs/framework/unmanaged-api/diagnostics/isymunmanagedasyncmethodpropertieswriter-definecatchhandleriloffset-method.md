---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce462c4e7e9c8fb11ee74a91f3ece2465a44a834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425437"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="fa1e3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa1e3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="fa1e3-103">Zaman uyumsuz yöntem sarmalar derleyicinin ürettiği catch işleyicisi için uzaklık IL ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa1e3-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="fa1e3-104">Oluşturulan yakalama IL uzaklığı hata ayıklayıcı tarafından bir kullanıcı kodu yönteminde oluşabilecek olsa bile kullanıcı olmayan kod kabul edildiğinde yakalama işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa1e3-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="fa1e3-105">Özellikle, bu yanıt olarak kullanıldığı bir **CatchHandlerFound** özel durum olayı.</span><span class="sxs-lookup"><span data-stu-id="fa1e3-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa1e3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa1e3-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa1e3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa1e3-107">Parameters</span></span>  
  
|<span data-ttu-id="fa1e3-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="fa1e3-108">Parameter</span></span>|<span data-ttu-id="fa1e3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa1e3-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="fa1e3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa1e3-110">Return Value</span></span>  
 <span data-ttu-id="fa1e3-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="fa1e3-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa1e3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa1e3-112">Requirements</span></span>  
 <span data-ttu-id="fa1e3-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fa1e3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1e3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa1e3-114">See Also</span></span>  
 [<span data-ttu-id="fa1e3-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa1e3-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
