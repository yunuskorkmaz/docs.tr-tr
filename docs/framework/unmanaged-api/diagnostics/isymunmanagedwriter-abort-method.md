---
title: ISymUnmanagedWriter::Abort Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 090183cad17aff6faf5e79639eadff086c1a26ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797468"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="ad975-102">ISymUnmanagedWriter::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad975-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="ad975-103">Sembolleri sembol deposuna taahhüt vermek zorunda kalmadan sembol yazıcı kapatır.</span><span class="sxs-lookup"><span data-stu-id="ad975-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="ad975-104">Bu çağrıdan sonra sembol yazıcısı güncelleştirmeleri daha fazla geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="ad975-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="ad975-105">Simgeleri işleyin ve sembol yazıcı kapatmak için kullanmak [Isymunmanagedwriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="ad975-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad975-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad975-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ad975-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ad975-107">Return Value</span></span>  
 <span data-ttu-id="ad975-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ad975-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad975-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad975-109">Requirements</span></span>  
 <span data-ttu-id="ad975-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ad975-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad975-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad975-111">See also</span></span>

- [<span data-ttu-id="ad975-112">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad975-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
