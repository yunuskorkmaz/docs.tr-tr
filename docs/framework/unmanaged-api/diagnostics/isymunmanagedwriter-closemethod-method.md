---
title: "ISymUnmanagedWriter::CloseMethod Yöntemi"
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
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 21c4cdd42613f5e8b60c39426b4f169a034ce7a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="3f5fe-102">ISymUnmanagedWriter::CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f5fe-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="3f5fe-103">Geçerli yöntemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="3f5fe-103">Closes the current method.</span></span> <span data-ttu-id="3f5fe-104">Bir yöntem kapatıldıktan sonra daha fazla simge içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3f5fe-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5fe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f5fe-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3f5fe-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f5fe-106">Return Value</span></span>  
 <span data-ttu-id="3f5fe-107">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3f5fe-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f5fe-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f5fe-108">Requirements</span></span>  
 <span data-ttu-id="3f5fe-109">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3f5fe-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5fe-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f5fe-110">See Also</span></span>  
 [<span data-ttu-id="3f5fe-111">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f5fe-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="3f5fe-112">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f5fe-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
