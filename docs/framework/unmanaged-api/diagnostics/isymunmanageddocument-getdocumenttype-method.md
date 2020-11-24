---
title: ISymUnmanagedDocument::GetDocumentType Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
ms.openlocfilehash: d30ee9318d76aaf3ad2cde789ae292aed54f457e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689686"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="2dc78-102">ISymUnmanagedDocument::GetDocumentType Metodu</span><span class="sxs-lookup"><span data-stu-id="2dc78-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>

<span data-ttu-id="2dc78-103">Bu belgenin belge türünü alır.</span><span class="sxs-lookup"><span data-stu-id="2dc78-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc78-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2dc78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dc78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2dc78-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="2dc78-106">dışı Belge türünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2dc78-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dc78-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2dc78-107">Return Value</span></span>  

 <span data-ttu-id="2dc78-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="2dc78-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc78-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dc78-109">See also</span></span>

- [<span data-ttu-id="2dc78-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2dc78-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
