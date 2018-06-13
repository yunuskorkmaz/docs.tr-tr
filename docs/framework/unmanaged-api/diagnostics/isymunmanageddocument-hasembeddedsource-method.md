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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 350aecb9f9c99c9aa44ae6df6d31c7cb69ae5760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430351"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="35ad8-102">ISymUnmanagedDocument::HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35ad8-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="35ad8-103">Döndürür `true` hata ayıklama simgeleri; katıştırılmış kaynak belge varsa, aksi takdirde, döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="35ad8-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ad8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35ad8-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35ad8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35ad8-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="35ad8-106">[out] Belge hata ayıklama simgeleri katıştırılmış kaynak olup olmadığını belirten bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35ad8-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35ad8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35ad8-107">Return Value</span></span>  
 <span data-ttu-id="35ad8-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="35ad8-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ad8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35ad8-109">See Also</span></span>  
 [<span data-ttu-id="35ad8-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35ad8-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
