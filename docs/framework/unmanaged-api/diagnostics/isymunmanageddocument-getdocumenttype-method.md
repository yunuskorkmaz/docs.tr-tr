---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: GetDocumentType yöntemi'
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
ms.openlocfilehash: cf2ceffccb33eb7cba0d45af203e12d1e4244f60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710328"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="99b3f-103">ISymUnmanagedDocument::GetDocumentType Metodu</span><span class="sxs-lookup"><span data-stu-id="99b3f-103">ISymUnmanagedDocument::GetDocumentType Method</span></span>

<span data-ttu-id="99b3f-104">Bu belgenin belge türünü alır.</span><span class="sxs-lookup"><span data-stu-id="99b3f-104">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b3f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99b3f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99b3f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99b3f-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="99b3f-107">dışı Belge türünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="99b3f-107">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99b3f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99b3f-108">Return Value</span></span>  

 <span data-ttu-id="99b3f-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="99b3f-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b3f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99b3f-110">See also</span></span>

- [<span data-ttu-id="99b3f-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99b3f-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
