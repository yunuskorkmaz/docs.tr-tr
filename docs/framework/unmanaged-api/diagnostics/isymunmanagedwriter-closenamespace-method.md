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
ms.openlocfilehash: 7a4ffc0c417ae839e5c97ffe6884bc3230a603b7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610112"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="2bd27-102">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2bd27-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="2bd27-103">En son açılan ad alanını kapatır.</span><span class="sxs-lookup"><span data-stu-id="2bd27-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd27-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2bd27-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2bd27-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2bd27-105">Return Value</span></span>  
 <span data-ttu-id="2bd27-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2bd27-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bd27-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bd27-107">Requirements</span></span>  
 <span data-ttu-id="2bd27-108">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2bd27-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd27-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bd27-109">See also</span></span>

- [<span data-ttu-id="2bd27-110">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bd27-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="2bd27-111">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2bd27-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
