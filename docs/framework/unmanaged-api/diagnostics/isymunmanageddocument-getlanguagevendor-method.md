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
ms.openlocfilehash: f5140462ae3c869d58187351d2e0ff11f7b6e179
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776697"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="a2816-102">ISymUnmanagedDocument::GetLanguageVendor Metodu</span><span class="sxs-lookup"><span data-stu-id="a2816-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="a2816-103">Bu belgenin dil satıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a2816-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2816-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2816-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2816-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2816-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a2816-106">[out] Dil satıcı alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2816-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2816-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2816-107">Return Value</span></span>  
 <span data-ttu-id="a2816-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="a2816-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2816-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2816-109">See also</span></span>

- [<span data-ttu-id="a2816-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2816-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
