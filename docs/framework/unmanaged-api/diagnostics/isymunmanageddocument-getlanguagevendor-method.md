---
title: ISymUnmanagedDocument::GetLanguageVendor Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25797822fc147c973ee06a52669aa9bf3c25422e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496254"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="0df76-102">ISymUnmanagedDocument::GetLanguageVendor Metodu</span><span class="sxs-lookup"><span data-stu-id="0df76-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="0df76-103">Bu belgenin dil satıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0df76-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df76-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0df76-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0df76-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0df76-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0df76-106">[out] Dil satıcı alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0df76-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0df76-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0df76-107">Return Value</span></span>  
 <span data-ttu-id="0df76-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="0df76-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df76-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0df76-109">See also</span></span>
- [<span data-ttu-id="0df76-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0df76-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
