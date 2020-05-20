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
ms.openlocfilehash: 5ec69aa06816b117fb05853001e59532629504c4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614610"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="23069-102">ISymUnmanagedDocument::GetDocumentType Metodu</span><span class="sxs-lookup"><span data-stu-id="23069-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="23069-103">Bu belgenin belge türünü alır.</span><span class="sxs-lookup"><span data-stu-id="23069-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23069-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="23069-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23069-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23069-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="23069-106">dışı Belge türünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="23069-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23069-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23069-107">Return Value</span></span>  
 <span data-ttu-id="23069-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="23069-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23069-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23069-109">See also</span></span>

- [<span data-ttu-id="23069-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23069-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
