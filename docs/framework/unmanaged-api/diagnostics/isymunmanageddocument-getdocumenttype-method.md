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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adad8854052d76476076e5e1357f6d3e2dec1052
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629481"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="52ccb-102">ISymUnmanagedDocument::GetDocumentType Metodu</span><span class="sxs-lookup"><span data-stu-id="52ccb-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="52ccb-103">Bu belgenin belge türünü alır.</span><span class="sxs-lookup"><span data-stu-id="52ccb-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52ccb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52ccb-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52ccb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52ccb-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="52ccb-106">[out] Belge türü alan bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52ccb-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52ccb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52ccb-107">Return Value</span></span>  
 <span data-ttu-id="52ccb-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="52ccb-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ccb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52ccb-109">See also</span></span>
- [<span data-ttu-id="52ccb-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52ccb-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
