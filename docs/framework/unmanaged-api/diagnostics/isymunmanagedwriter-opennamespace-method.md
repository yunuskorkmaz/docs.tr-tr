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
ms.openlocfilehash: 02f57fdbbc1ea9a391d9c58c7ab49af0ef02f001
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426968"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="7d22d-102">ISymUnmanagedWriter::OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d22d-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="7d22d-103">Yeni bir ad alanı açılır.</span><span class="sxs-lookup"><span data-stu-id="7d22d-103">Opens a new namespace.</span></span> <span data-ttu-id="7d22d-104">Yöntem veya bir ad alanı kaplar değişkenleri tanımlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="7d22d-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="7d22d-105">Ad alanları iç içe.</span><span class="sxs-lookup"><span data-stu-id="7d22d-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d22d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d22d-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d22d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d22d-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="7d22d-108">[in] Yeni ad alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d22d-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d22d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d22d-109">Return Value</span></span>  
 <span data-ttu-id="7d22d-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7d22d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d22d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d22d-111">Requirements</span></span>  
 <span data-ttu-id="7d22d-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7d22d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d22d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d22d-113">See Also</span></span>  
 [<span data-ttu-id="7d22d-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d22d-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="7d22d-115">CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d22d-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
