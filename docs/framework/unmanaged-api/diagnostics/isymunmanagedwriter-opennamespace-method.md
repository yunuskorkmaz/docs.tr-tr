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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf0fbcbf6af53c6a7865e2a2cf7874ea44581e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474624"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="96ea7-102">ISymUnmanagedWriter::OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96ea7-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="96ea7-103">Yeni bir ad alanı açılır.</span><span class="sxs-lookup"><span data-stu-id="96ea7-103">Opens a new namespace.</span></span> <span data-ttu-id="96ea7-104">Yöntem veya bir ad alanı kaplayan değişkenleri tanımlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="96ea7-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="96ea7-105">Ad alanları yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="96ea7-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ea7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96ea7-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96ea7-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96ea7-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="96ea7-108">[in] Yeni ad alanı adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96ea7-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96ea7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="96ea7-109">Return Value</span></span>  
 <span data-ttu-id="96ea7-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="96ea7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ea7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96ea7-111">Requirements</span></span>  
 <span data-ttu-id="96ea7-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="96ea7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ea7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96ea7-113">See also</span></span>
- [<span data-ttu-id="96ea7-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96ea7-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="96ea7-115">CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96ea7-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
