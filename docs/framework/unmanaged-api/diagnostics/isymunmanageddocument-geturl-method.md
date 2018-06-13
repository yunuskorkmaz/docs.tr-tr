---
title: ISymUnmanagedDocument::GetURL Metodu
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
ms.openlocfilehash: 5a447de2bb01e7bbf838ef5443e3ae7951bf8226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431373"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="9e405-102">ISymUnmanagedDocument::GetURL Metodu</span><span class="sxs-lookup"><span data-stu-id="9e405-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="9e405-103">Bu belge için Tekdüzen Kaynak Konum Belirleyici (URL) döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e405-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e405-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e405-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e405-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e405-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="9e405-106">[in] Karakter, boyutu, `szURL` arabellek.</span><span class="sxs-lookup"><span data-stu-id="9e405-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="9e405-107">[out] Bir işaretçi bir değişkene null sonlandırma dahil olmak üzere URL'yi boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="9e405-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="9e405-108">[out] URL'sini içeren arabelleği.</span><span class="sxs-lookup"><span data-stu-id="9e405-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e405-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e405-109">Return Value</span></span>  
 <span data-ttu-id="9e405-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9e405-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e405-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e405-111">See Also</span></span>  
 [<span data-ttu-id="9e405-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e405-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
