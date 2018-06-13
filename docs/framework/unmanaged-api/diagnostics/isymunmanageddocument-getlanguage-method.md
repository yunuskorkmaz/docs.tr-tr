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
ms.openlocfilehash: 98c981a10a07d035300349cc8687b3201ed70927
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424303"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="898cb-102">ISymUnmanagedDocument::GetLanguage Metodu</span><span class="sxs-lookup"><span data-stu-id="898cb-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="898cb-103">Bu belge dil tanımlayıcısını alır</span><span class="sxs-lookup"><span data-stu-id="898cb-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="898cb-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="898cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="898cb-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="898cb-106">[out] Bir işaretçi bir değişkene dil tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="898cb-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="898cb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="898cb-107">Return Value</span></span>  
 <span data-ttu-id="898cb-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="898cb-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898cb-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="898cb-109">See Also</span></span>  
 [<span data-ttu-id="898cb-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="898cb-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
