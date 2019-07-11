---
title: ISymUnmanagedWriter::UsingNamespace Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0076b70c85c21f0c4b1fb140b15000f99dbff742
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755139"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="7772c-102">ISymUnmanagedWriter::UsingNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7772c-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="7772c-103">Tam ad alanı adı verilen açık sözlü kapsamda kullanılmakta olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7772c-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="7772c-104">Ad alanı içinde açık olan kapsamlardan devralır tüm kapsamlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7772c-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="7772c-105">Geçerli kapsamdaki kapatma ad alanı kullanımını durdurur.</span><span class="sxs-lookup"><span data-stu-id="7772c-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7772c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7772c-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7772c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7772c-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="7772c-108">[in] Ad alanının tam adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7772c-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7772c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7772c-109">Return Value</span></span>  
 <span data-ttu-id="7772c-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7772c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7772c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7772c-111">Requirements</span></span>  
 <span data-ttu-id="7772c-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7772c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7772c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7772c-113">See also</span></span>

- [<span data-ttu-id="7772c-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7772c-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
