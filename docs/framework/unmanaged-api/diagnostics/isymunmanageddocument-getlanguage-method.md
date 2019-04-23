---
title: ISymUnmanagedDocument::GetLanguage Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ce47953358b7025e30080fbbaf288a6c0e879d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104604"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="7c107-102">ISymUnmanagedDocument::GetLanguage Metodu</span><span class="sxs-lookup"><span data-stu-id="7c107-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="7c107-103">Bu belgenin dil tanımlayıcısını alır</span><span class="sxs-lookup"><span data-stu-id="7c107-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c107-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c107-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c107-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c107-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7c107-106">[out] Bir işaretçi bir değişkene dil tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="7c107-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c107-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7c107-107">Return Value</span></span>  
 <span data-ttu-id="7c107-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="7c107-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c107-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c107-109">See also</span></span>

- [<span data-ttu-id="7c107-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c107-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
