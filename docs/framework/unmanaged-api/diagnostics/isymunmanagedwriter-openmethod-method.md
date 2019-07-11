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
ms.openlocfilehash: 25178b5ea27aac7229ab51a167283d955b89addc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777266"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="1c90f-102">ISymUnmanagedWriter::OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c90f-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="1c90f-103">Hangi sembolün üretileceği bilgi yayılan bir yöntem açılır.</span><span class="sxs-lookup"><span data-stu-id="1c90f-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="1c90f-104">Belirtilen yöntem geçerli yöntem dizi noktaları, parametreler ve sözcük kapsamları tanımlamak çağrılar için olur.</span><span class="sxs-lookup"><span data-stu-id="1c90f-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="1c90f-105">Örtük bir sözcük kapsamı tüm yöntemi etrafında yoktur.</span><span class="sxs-lookup"><span data-stu-id="1c90f-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="1c90f-106">Daha önce kapatılan bir yöntem yeniden açmayı, bu yöntem için önceden tanımlanmış semboller siler.</span><span class="sxs-lookup"><span data-stu-id="1c90f-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="1c90f-107">Bir kerede yalnızca bir açık yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c90f-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c90f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c90f-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c90f-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c90f-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="1c90f-110">[in] Meta veri belirteci açılması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c90f-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c90f-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1c90f-111">Return Value</span></span>  
 <span data-ttu-id="1c90f-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1c90f-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c90f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c90f-113">Requirements</span></span>  
 <span data-ttu-id="1c90f-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1c90f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c90f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c90f-115">See also</span></span>

- [<span data-ttu-id="1c90f-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c90f-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="1c90f-117">CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c90f-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="1c90f-118">OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c90f-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
