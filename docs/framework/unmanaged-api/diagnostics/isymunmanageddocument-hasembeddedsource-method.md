---
title: ISymUnmanagedDocument::HasEmbeddedSource Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: 533d8a5481fe9ba7e7e65775229156a9cc3cf4d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449115"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="008f0-102">ISymUnmanagedDocument::HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="008f0-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="008f0-103">Belge hata ayıklama sembollerine katıştırılmış kaynak içeriyorsa `true` döndürür; Aksi takdirde, `false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="008f0-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="008f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="008f0-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="008f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="008f0-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="008f0-106">dışı Belgenin hata ayıklama sembollerine gömülü kaynak olup olmadığını gösteren bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="008f0-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="008f0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="008f0-107">Return Value</span></span>  
 <span data-ttu-id="008f0-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="008f0-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008f0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="008f0-109">See also</span></span>

- [<span data-ttu-id="008f0-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="008f0-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
