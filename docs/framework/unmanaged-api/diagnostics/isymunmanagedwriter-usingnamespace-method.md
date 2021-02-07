---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedwriter:: UsingNamespace Yöntemi'
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
ms.openlocfilehash: e7d56cded125aac6154d4315c587f58f946a9a82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761960"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="5953a-103">ISymUnmanagedWriter::UsingNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5953a-103">ISymUnmanagedWriter::UsingNamespace Method</span></span>

<span data-ttu-id="5953a-104">Verilen tam ad alanı adının şu anda açık olan sözlü kapsam içinde kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5953a-104">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="5953a-105">Ad alanı şu anda açık olan kapsamdan devraldığı tüm kapsamlar içinde kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="5953a-105">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="5953a-106">Geçerli kapsamın kapatılması, ad alanının kullanımını da durdurur.</span><span class="sxs-lookup"><span data-stu-id="5953a-106">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5953a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5953a-107">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5953a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5953a-108">Parameters</span></span>  

 `fullName`  
 <span data-ttu-id="5953a-109">'ndaki Ad alanının tam adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5953a-109">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5953a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5953a-110">Return Value</span></span>  

 <span data-ttu-id="5953a-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5953a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5953a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5953a-112">Requirements</span></span>  

 <span data-ttu-id="5953a-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5953a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5953a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5953a-114">See also</span></span>

- [<span data-ttu-id="5953a-115">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5953a-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
