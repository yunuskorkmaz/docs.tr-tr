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
ms.openlocfilehash: acff919cbeb6b5d71197664139cdc9212961e314
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629520"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="62f7f-102">ISymUnmanagedDocument::HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62f7f-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="62f7f-103">Döndürür `true` hata ayıklama sembolleri; katıştırılmış kaynak belge varsa, aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="62f7f-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f7f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62f7f-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62f7f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62f7f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="62f7f-106">[out] Belge hata ayıklama sembolleri gömülü kaynak olup olmadığını belirten bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62f7f-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62f7f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="62f7f-107">Return Value</span></span>  
 <span data-ttu-id="62f7f-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="62f7f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f7f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62f7f-109">See also</span></span>
- [<span data-ttu-id="62f7f-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62f7f-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
