---
title: ISymUnmanagedDocument::GetURL Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b42bb72975fad4c1830a961f83d9e3065d055b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187466"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="341db-102">ISymUnmanagedDocument::GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="341db-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="341db-103">Tekdüzen Kaynak Konum Belirleyicisi (URL)'için bu belgeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="341db-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="341db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="341db-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="341db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="341db-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="341db-106">[in] Karakter cinsinden boyutu, `szURL` arabellek.</span><span class="sxs-lookup"><span data-stu-id="341db-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="341db-107">[out] Bir işaretçi bir değişkene null sonlandırma dahil olmak üzere URL'yi boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="341db-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="341db-108">[out] URL'sini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="341db-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="341db-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="341db-109">Return Value</span></span>  
 <span data-ttu-id="341db-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="341db-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341db-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="341db-111">See also</span></span>

- [<span data-ttu-id="341db-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="341db-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
