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
ms.openlocfilehash: 4429d49a489871a8993d9f841d9c5e7e37a53b5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689685"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="8d68e-102">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d68e-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="8d68e-103">Kapatır, ad alanı en son açıldı.</span><span class="sxs-lookup"><span data-stu-id="8d68e-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d68e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d68e-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8d68e-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8d68e-105">Return Value</span></span>  
 <span data-ttu-id="8d68e-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8d68e-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d68e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d68e-107">Requirements</span></span>  
 <span data-ttu-id="8d68e-108">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8d68e-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d68e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d68e-109">See also</span></span>
- [<span data-ttu-id="8d68e-110">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d68e-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="8d68e-111">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d68e-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
