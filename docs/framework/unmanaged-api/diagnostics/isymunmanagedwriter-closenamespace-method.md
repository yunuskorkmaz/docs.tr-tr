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
ms.openlocfilehash: 66f8804c911e053758442670afb3c3f27d0f7453
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986095"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="e315d-102">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e315d-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="e315d-103">Kapatır, ad alanı en son açıldı.</span><span class="sxs-lookup"><span data-stu-id="e315d-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e315d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e315d-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e315d-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e315d-105">Return Value</span></span>  
 <span data-ttu-id="e315d-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e315d-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e315d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e315d-107">Requirements</span></span>  
 <span data-ttu-id="e315d-108">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e315d-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e315d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e315d-109">See also</span></span>

- [<span data-ttu-id="e315d-110">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e315d-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="e315d-111">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e315d-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
