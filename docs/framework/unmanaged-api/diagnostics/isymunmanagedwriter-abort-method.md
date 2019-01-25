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
ms.openlocfilehash: b4c79cb3df37a9ed10e46567be63aad29fee37c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550194"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="33b4d-102">ISymUnmanagedWriter::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33b4d-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="33b4d-103">Sembolleri sembol deposuna taahhüt vermek zorunda kalmadan sembol yazıcı kapatır.</span><span class="sxs-lookup"><span data-stu-id="33b4d-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="33b4d-104">Bu çağrıdan sonra sembol yazıcısı güncelleştirmeleri daha fazla geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="33b4d-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="33b4d-105">Simgeleri işleyin ve sembol yazıcı kapatmak için kullanmak [Isymunmanagedwriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="33b4d-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b4d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33b4d-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="33b4d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="33b4d-107">Return Value</span></span>  
 <span data-ttu-id="33b4d-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="33b4d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33b4d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33b4d-109">Requirements</span></span>  
 <span data-ttu-id="33b4d-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33b4d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b4d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33b4d-111">See also</span></span>
- [<span data-ttu-id="33b4d-112">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33b4d-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
