---
title: ISymUnmanagedWriter::OpenNamespace Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: 2f64f9f4bde3119f9f089becec5a36d69ed43596
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730067"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="ae901-102">ISymUnmanagedWriter::OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae901-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>

<span data-ttu-id="ae901-103">Yeni bir ad alanı açar.</span><span class="sxs-lookup"><span data-stu-id="ae901-103">Opens a new namespace.</span></span> <span data-ttu-id="ae901-104">Bir ad alanı kaplayan yöntemleri veya değişkenleri tanımlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ae901-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="ae901-105">Ad alanları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae901-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae901-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ae901-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae901-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae901-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="ae901-108">'ndaki Yeni ad alanının adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae901-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae901-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae901-109">Return Value</span></span>  

 <span data-ttu-id="ae901-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ae901-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae901-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae901-111">Requirements</span></span>  

 <span data-ttu-id="ae901-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ae901-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae901-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae901-113">See also</span></span>

- [<span data-ttu-id="ae901-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae901-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="ae901-115">CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae901-115">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)
