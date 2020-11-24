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
ms.openlocfilehash: 13a433157e0c92653edf234f1f1f885270196ffd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686416"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="8eb10-102">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eb10-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>

<span data-ttu-id="8eb10-103">En son açılan ad alanını kapatır.</span><span class="sxs-lookup"><span data-stu-id="8eb10-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb10-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8eb10-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8eb10-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8eb10-105">Return Value</span></span>  

 <span data-ttu-id="8eb10-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8eb10-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb10-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8eb10-107">Requirements</span></span>  

 <span data-ttu-id="8eb10-108">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8eb10-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb10-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eb10-109">See also</span></span>

- [<span data-ttu-id="8eb10-110">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eb10-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="8eb10-111">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eb10-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
