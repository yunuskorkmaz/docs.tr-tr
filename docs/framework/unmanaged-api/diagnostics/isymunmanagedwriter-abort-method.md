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
ms.openlocfilehash: eb6a3e65b1f1d59cde3bff99e491bcf09816c8ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428064"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="35305-102">ISymUnmanagedWriter::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35305-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="35305-103">Sembol yazan sembol deposu simgeleri kaydetmeden kapatır.</span><span class="sxs-lookup"><span data-stu-id="35305-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="35305-104">Bu çağrısından sonra simge yazan güncelleştirmeler için daha fazla geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="35305-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="35305-105">Simgeler tamamlama ve sembol yazıcı kapatmak için kullanın [Isymunmanagedwriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="35305-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35305-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35305-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="35305-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35305-107">Return Value</span></span>  
 <span data-ttu-id="35305-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="35305-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35305-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35305-109">Requirements</span></span>  
 <span data-ttu-id="35305-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="35305-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35305-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35305-111">See Also</span></span>  
 [<span data-ttu-id="35305-112">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35305-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
