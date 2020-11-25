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
ms.openlocfilehash: c862b6d3bfa415b622b68898db1ff30c6759e8f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726944"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="943e1-102">ISymUnmanagedDocument::GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="943e1-102">ISymUnmanagedDocument::GetURL Method</span></span>

<span data-ttu-id="943e1-103">Bu belge için Tekdüzen Kaynak Konumlandırıcı 'sını (URL) döndürür.</span><span class="sxs-lookup"><span data-stu-id="943e1-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943e1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="943e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="943e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="943e1-105">Parameters</span></span>  

 `cchUrl`  
 <span data-ttu-id="943e1-106">'ndaki Arabelleğin karakter cinsinden boyutu `szURL` .</span><span class="sxs-lookup"><span data-stu-id="943e1-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="943e1-107">dışı Null sonlandırma dahil olmak üzere URL boyutunu alan bir değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="943e1-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="943e1-108">dışı URL 'YI içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="943e1-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="943e1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="943e1-109">Return Value</span></span>  

 <span data-ttu-id="943e1-110">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="943e1-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943e1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="943e1-111">See also</span></span>

- [<span data-ttu-id="943e1-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="943e1-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
