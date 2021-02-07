---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedwriter:: OpenNamespace yöntemi'
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
ms.openlocfilehash: ab848e44dfda1f5caaa92bfd3376bdcbd67d8a9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762129"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="c4737-103">ISymUnmanagedWriter::OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4737-103">ISymUnmanagedWriter::OpenNamespace Method</span></span>

<span data-ttu-id="c4737-104">Yeni bir ad alanı açar.</span><span class="sxs-lookup"><span data-stu-id="c4737-104">Opens a new namespace.</span></span> <span data-ttu-id="c4737-105">Bir ad alanı kaplayan yöntemleri veya değişkenleri tanımlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="c4737-105">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="c4737-106">Ad alanları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4737-106">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4737-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4737-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4737-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4737-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="c4737-109">'ndaki Yeni ad alanının adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c4737-109">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4737-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c4737-110">Return Value</span></span>  

 <span data-ttu-id="c4737-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c4737-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4737-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4737-112">Requirements</span></span>  

 <span data-ttu-id="c4737-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c4737-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4737-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4737-114">See also</span></span>

- [<span data-ttu-id="c4737-115">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4737-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c4737-116">CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4737-116">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)
