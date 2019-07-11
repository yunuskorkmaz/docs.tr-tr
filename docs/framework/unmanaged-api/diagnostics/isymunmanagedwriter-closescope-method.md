---
title: ISymUnmanagedWriter::CloseScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a9edfa2f8888480c72f290ee237972f3a0ed912
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778125"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="6eb0a-102">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6eb0a-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="6eb0a-103">Geçerli sözcük kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6eb0a-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eb0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6eb0a-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="6eb0a-106">[in] Başlangıçtan itibaren bayt sözlü kapsamda son yönergenin bitiminden noktada yönteminin uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eb0a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6eb0a-107">Return Value</span></span>  
 <span data-ttu-id="6eb0a-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb0a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6eb0a-109">Remarks</span></span>  
 <span data-ttu-id="6eb0a-110">Bir kapsam kapatıldıktan sonra daha fazla değişken içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="6eb0a-111">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılabilecek donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) daha sonra bir kapsamı tanımlamak için başlangıç ve bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="6eb0a-112">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve `ISymUnmanagedWriter::CloseScope` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="6eb0a-113">Kapsam tanımlayıcılar yalnızca geçerli yöntemi içinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb0a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6eb0a-114">Requirements</span></span>  
 <span data-ttu-id="6eb0a-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6eb0a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb0a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6eb0a-116">See also</span></span>

- [<span data-ttu-id="6eb0a-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6eb0a-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
