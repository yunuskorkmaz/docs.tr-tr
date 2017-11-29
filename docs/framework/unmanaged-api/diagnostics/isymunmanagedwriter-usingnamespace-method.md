---
title: "ISymUnmanagedWriter::UsingNamespace Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.UsingNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9bfd5ca0c22a9b4da1acb1f93b29150beba865a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="02beb-102">ISymUnmanagedWriter::UsingNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02beb-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="02beb-103">Verilen tam ad alanı adı şu anda açık sözcük kapsamında kullanılmakta olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02beb-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="02beb-104">Ad alanı, açık olan kapsamlardan devralır tüm kapsamlarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02beb-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="02beb-105">Geçerli kapsamdaki kapatma ad alanı kullanımını de durdurulur.</span><span class="sxs-lookup"><span data-stu-id="02beb-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02beb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02beb-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02beb-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02beb-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="02beb-108">[in] Ad alanının tam adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="02beb-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02beb-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="02beb-109">Return Value</span></span>  
 <span data-ttu-id="02beb-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="02beb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02beb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02beb-111">Requirements</span></span>  
 <span data-ttu-id="02beb-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="02beb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02beb-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02beb-113">See Also</span></span>  
 [<span data-ttu-id="02beb-114">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="02beb-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
