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
ms.openlocfilehash: 620d303bcd33a4d04155850ec2c1b6293bf788d1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493264"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="ca4d6-102">ISymUnmanagedDocument::HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca4d6-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="ca4d6-103">Döndürür `true` hata ayıklama sembolleri; katıştırılmış kaynak belge varsa, aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="ca4d6-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca4d6-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca4d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca4d6-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ca4d6-106">[out] Belge hata ayıklama sembolleri gömülü kaynak olup olmadığını belirten bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ca4d6-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca4d6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ca4d6-107">Return Value</span></span>  
 <span data-ttu-id="ca4d6-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="ca4d6-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4d6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca4d6-109">See also</span></span>
- [<span data-ttu-id="ca4d6-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca4d6-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
