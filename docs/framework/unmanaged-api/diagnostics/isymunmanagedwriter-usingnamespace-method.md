---
title: "ISymUnmanagedWriter::UsingNamespace Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d02a36a43e8a831fbbef051f5898696d4d8e04c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="e07d9-102">ISymUnmanagedWriter::UsingNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e07d9-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="e07d9-103">Verilen tam ad alanı adı şu anda açık sözcük kapsamında kullanılmakta olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e07d9-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="e07d9-104">Ad alanı, açık olan kapsamlardan devralır tüm kapsamlarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e07d9-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="e07d9-105">Geçerli kapsamdaki kapatma ad alanı kullanımını de durdurulur.</span><span class="sxs-lookup"><span data-stu-id="e07d9-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07d9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e07d9-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e07d9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e07d9-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="e07d9-108">[in] Ad alanının tam adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e07d9-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e07d9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e07d9-109">Return Value</span></span>  
 <span data-ttu-id="e07d9-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e07d9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07d9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e07d9-111">Requirements</span></span>  
 <span data-ttu-id="e07d9-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e07d9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07d9-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e07d9-113">See Also</span></span>  
 [<span data-ttu-id="e07d9-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e07d9-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
