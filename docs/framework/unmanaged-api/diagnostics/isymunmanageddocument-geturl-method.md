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
ms.openlocfilehash: 5d8bc90cc07c2390cc83860b8009a3705f927e80
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776670"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="720b2-102">ISymUnmanagedDocument::GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="720b2-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="720b2-103">Tekdüzen Kaynak Konum Belirleyicisi (URL)'için bu belgeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="720b2-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="720b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="720b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="720b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="720b2-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="720b2-106">[in] Karakter cinsinden boyutu, `szURL` arabellek.</span><span class="sxs-lookup"><span data-stu-id="720b2-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="720b2-107">[out] Bir işaretçi bir değişkene null sonlandırma dahil olmak üzere URL'yi boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="720b2-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="720b2-108">[out] URL'sini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="720b2-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="720b2-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="720b2-109">Return Value</span></span>  
 <span data-ttu-id="720b2-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="720b2-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720b2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="720b2-111">See also</span></span>

- [<span data-ttu-id="720b2-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="720b2-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
