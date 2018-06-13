---
title: ISymUnmanagedWriter::OpenMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc41acd6a4f2ef2557d3b39523c5e398c887c454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427914"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="c88ab-102">ISymUnmanagedWriter::OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88ab-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="c88ab-103">Hangi sembolün bilgi yayılan bir yöntem açar.</span><span class="sxs-lookup"><span data-stu-id="c88ab-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="c88ab-104">Belirtilen yöntem geçerli yöntem sıralama noktaları, parametreleri ve sözcük kapsamları tanımlamak çağrıları için olur.</span><span class="sxs-lookup"><span data-stu-id="c88ab-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="c88ab-105">Tüm yöntemi geçici örtük bir sözcük kapsamı yok.</span><span class="sxs-lookup"><span data-stu-id="c88ab-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="c88ab-106">Daha önce kapatıldı bir yöntem açmayı bu yöntem için önceden tanımlanmış semboller siler.</span><span class="sxs-lookup"><span data-stu-id="c88ab-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="c88ab-107">Aynı anda yalnızca bir açık yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="c88ab-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c88ab-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c88ab-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c88ab-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c88ab-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="c88ab-110">[in] Yöntemin açılması meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="c88ab-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c88ab-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c88ab-111">Return Value</span></span>  
 <span data-ttu-id="c88ab-112">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c88ab-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c88ab-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c88ab-113">Requirements</span></span>  
 <span data-ttu-id="c88ab-114">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c88ab-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c88ab-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c88ab-115">See Also</span></span>  
 [<span data-ttu-id="c88ab-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c88ab-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="c88ab-117">CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88ab-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="c88ab-118">OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88ab-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
