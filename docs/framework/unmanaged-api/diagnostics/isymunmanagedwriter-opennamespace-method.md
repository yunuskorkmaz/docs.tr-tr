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
ms.openlocfilehash: acbd49de7362d9c05a609a2d870af100637e10ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427911"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="be04c-102">ISymUnmanagedWriter::OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be04c-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="be04c-103">Opens a new namespace.</span><span class="sxs-lookup"><span data-stu-id="be04c-103">Opens a new namespace.</span></span> <span data-ttu-id="be04c-104">Call this method before defining methods or variables that occupy a namespace.</span><span class="sxs-lookup"><span data-stu-id="be04c-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="be04c-105">Namespaces can be nested.</span><span class="sxs-lookup"><span data-stu-id="be04c-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be04c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be04c-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be04c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be04c-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="be04c-108">[in] A pointer to the name of the new namespace.</span><span class="sxs-lookup"><span data-stu-id="be04c-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be04c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be04c-109">Return Value</span></span>  
 <span data-ttu-id="be04c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="be04c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be04c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be04c-111">Requirements</span></span>  
 <span data-ttu-id="be04c-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="be04c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be04c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be04c-113">See also</span></span>

- [<span data-ttu-id="be04c-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be04c-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="be04c-115">CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be04c-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
