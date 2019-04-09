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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104604"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="ee110-102">ISymUnmanagedDocument::GetLanguage Metodu</span><span class="sxs-lookup"><span data-stu-id="ee110-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="ee110-103">Bu belgenin dil tanımlayıcısını alır</span><span class="sxs-lookup"><span data-stu-id="ee110-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee110-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee110-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee110-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee110-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ee110-106">[out] Bir işaretçi bir değişkene dil tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="ee110-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee110-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ee110-107">Return Value</span></span>  
 <span data-ttu-id="ee110-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="ee110-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee110-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee110-109">See also</span></span>

- [<span data-ttu-id="ee110-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee110-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
