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
ms.openlocfilehash: e4348cc59924b65b6c6bb53a9c2a98f1a1161b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614740"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="20eb1-102">ISymUnmanagedWriter::UsingNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20eb1-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="20eb1-103">Verilen tam ad alanı adının şu anda açık olan sözlü kapsam içinde kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="20eb1-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="20eb1-104">Ad alanı şu anda açık olan kapsamdan devraldığı tüm kapsamlar içinde kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="20eb1-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="20eb1-105">Geçerli kapsamın kapatılması, ad alanının kullanımını da durdurur.</span><span class="sxs-lookup"><span data-stu-id="20eb1-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20eb1-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="20eb1-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20eb1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20eb1-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="20eb1-108">'ndaki Ad alanının tam adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20eb1-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20eb1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20eb1-109">Return Value</span></span>  
 <span data-ttu-id="20eb1-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="20eb1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20eb1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20eb1-111">Requirements</span></span>  
 <span data-ttu-id="20eb1-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="20eb1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20eb1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20eb1-113">See also</span></span>

- [<span data-ttu-id="20eb1-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20eb1-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
