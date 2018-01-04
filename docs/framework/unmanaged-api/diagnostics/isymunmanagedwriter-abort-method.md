---
title: "ISymUnmanagedWriter::Abort Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Abort
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8013bf2118a73a8b5eb8a5b160f2655a83382efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="5dfae-102">ISymUnmanagedWriter::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5dfae-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="5dfae-103">Sembol yazan sembol deposu simgeleri kaydetmeden kapatır.</span><span class="sxs-lookup"><span data-stu-id="5dfae-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="5dfae-104">Bu çağrısından sonra simge yazan güncelleştirmeler için daha fazla geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="5dfae-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="5dfae-105">Simgeler tamamlama ve sembol yazıcı kapatmak için kullanın [Isymunmanagedwriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="5dfae-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dfae-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5dfae-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5dfae-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5dfae-107">Return Value</span></span>  
 <span data-ttu-id="5dfae-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5dfae-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dfae-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5dfae-109">Requirements</span></span>  
 <span data-ttu-id="5dfae-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5dfae-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dfae-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5dfae-111">See Also</span></span>  
 [<span data-ttu-id="5dfae-112">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5dfae-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
