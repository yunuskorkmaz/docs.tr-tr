---
title: ISymUnmanagedDocument::GetLanguageVendor Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguageVendor
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 72fffae9995f44be9a9359c16bb876d79c9a8242
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="b3801-102">ISymUnmanagedDocument::GetLanguageVendor Metodu</span><span class="sxs-lookup"><span data-stu-id="b3801-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="b3801-103">Bu belgenin dil satıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b3801-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3801-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3801-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3801-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3801-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b3801-106">[out] Bir işaretçi bir değişkene dil satıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b3801-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3801-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3801-107">Return Value</span></span>  
 <span data-ttu-id="b3801-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="b3801-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3801-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3801-109">See Also</span></span>  
 [<span data-ttu-id="b3801-110">Isymunmanageddocument arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3801-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
