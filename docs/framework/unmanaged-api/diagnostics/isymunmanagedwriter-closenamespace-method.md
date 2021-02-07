---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: CloseNamespace yöntemi'
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
ms.openlocfilehash: c552d8bc86ab2bbd93918fdd6be3f880b3d83178
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762571"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="c3b5c-103">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3b5c-103">ISymUnmanagedWriter::CloseNamespace Method</span></span>

<span data-ttu-id="c3b5c-104">En son açılan ad alanını kapatır.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-104">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b5c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3b5c-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c3b5c-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3b5c-106">Return Value</span></span>  

 <span data-ttu-id="c3b5c-107">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b5c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3b5c-108">Requirements</span></span>  

 <span data-ttu-id="c3b5c-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c3b5c-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b5c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-110">See also</span></span>

- [<span data-ttu-id="c3b5c-111">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3b5c-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c3b5c-112">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3b5c-112">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
