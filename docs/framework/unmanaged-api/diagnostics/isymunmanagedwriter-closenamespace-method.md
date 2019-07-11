---
title: ISymUnmanagedWriter::CloseNamespace Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ed618847d398bb4dcccb8ecebabdc947390c874
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778167"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="67c25-102">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67c25-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="67c25-103">Kapatır, ad alanı en son açıldı.</span><span class="sxs-lookup"><span data-stu-id="67c25-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67c25-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="67c25-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="67c25-105">Return Value</span></span>  
 <span data-ttu-id="67c25-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="67c25-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67c25-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67c25-107">Requirements</span></span>  
 <span data-ttu-id="67c25-108">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="67c25-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c25-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67c25-109">See also</span></span>

- [<span data-ttu-id="67c25-110">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67c25-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="67c25-111">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67c25-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
