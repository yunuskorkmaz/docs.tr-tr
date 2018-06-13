---
title: ISymUnmanagedDispose::Destroy Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d4b5f94bdbb7319cef14c8b86f8ea995df7ff21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424488"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="3f4af-102">ISymUnmanagedDispose::Destroy Metodu</span><span class="sxs-lookup"><span data-stu-id="3f4af-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="3f4af-103">Tüm iç başvuruları sürüm ve tüm sonraki yöntem çağrılarını hatası dönmek temel alınan nesnenin neden olur.</span><span class="sxs-lookup"><span data-stu-id="3f4af-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f4af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f4af-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3f4af-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f4af-105">Return Value</span></span>  
 <span data-ttu-id="3f4af-106">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3f4af-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f4af-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f4af-107">Requirements</span></span>  
 <span data-ttu-id="3f4af-108">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3f4af-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4af-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f4af-109">See Also</span></span>  
 [<span data-ttu-id="3f4af-110">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f4af-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
