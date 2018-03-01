---
title: "ISymUnmanagedWriter::Close Yöntemi"
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
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70f710802862c3237cbd67693f8366946926891e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="c7f37-102">ISymUnmanagedWriter::Close Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7f37-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="c7f37-103">Sembol yazan simgeleri sembol deposu uyguladıktan sonra kapatır.</span><span class="sxs-lookup"><span data-stu-id="c7f37-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f37-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7f37-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c7f37-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7f37-105">Return Value</span></span>  
 <span data-ttu-id="c7f37-106">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c7f37-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7f37-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7f37-107">Remarks</span></span>  
 <span data-ttu-id="c7f37-108">Bu çağrısından sonra simge yazan güncelleştirmeler için daha fazla geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="c7f37-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="c7f37-109">Sembol yazan simgeleri kaydetmeden kapatmak için kullanın [Isymunmanagedwriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="c7f37-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7f37-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7f37-110">Requirements</span></span>  
 <span data-ttu-id="c7f37-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c7f37-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f37-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7f37-112">See Also</span></span>  
 [<span data-ttu-id="c7f37-113">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7f37-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
