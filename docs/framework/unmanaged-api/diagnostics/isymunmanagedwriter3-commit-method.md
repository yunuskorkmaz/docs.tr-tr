---
title: ISymUnmanagedWriter3::Commit Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38d9c3eeb5cdb8b15ef5306a641910f2f4bcc9cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372353"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="739de-102">ISymUnmanagedWriter3::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="739de-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="739de-103">Şu ana kadar akışa yazılan değişiklikleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="739de-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="739de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="739de-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="739de-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="739de-105">Return Value</span></span>  
 <span data-ttu-id="739de-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="739de-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="739de-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="739de-107">Requirements</span></span>  
 <span data-ttu-id="739de-108">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="739de-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739de-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="739de-109">See also</span></span>
- [<span data-ttu-id="739de-110">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="739de-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
