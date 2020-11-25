---
title: ISymUnmanagedReader::GetDocument Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 4604d78f66b872a30457c51bf65890caf613c4fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707639"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="8de2d-102">ISymUnmanagedReader::GetDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="8de2d-102">ISymUnmanagedReader::GetDocument Method</span></span>

<span data-ttu-id="8de2d-103">Bir belge bulur.</span><span class="sxs-lookup"><span data-stu-id="8de2d-103">Finds a document.</span></span> <span data-ttu-id="8de2d-104">Belge dili, satıcı ve tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8de2d-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de2d-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8de2d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8de2d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8de2d-106">Parameters</span></span>  

 `url`  
 <span data-ttu-id="8de2d-107">'ndaki Belgeyi tanımlayan URL.</span><span class="sxs-lookup"><span data-stu-id="8de2d-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="8de2d-108">'ndaki Belge dili.</span><span class="sxs-lookup"><span data-stu-id="8de2d-108">[in] The document language.</span></span> <span data-ttu-id="8de2d-109">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8de2d-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="8de2d-110">'ndaki Belge dili için satıcının kimliği.</span><span class="sxs-lookup"><span data-stu-id="8de2d-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="8de2d-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8de2d-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="8de2d-112">'ndaki Belge türü.</span><span class="sxs-lookup"><span data-stu-id="8de2d-112">[in] The type of the document.</span></span> <span data-ttu-id="8de2d-113">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8de2d-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8de2d-114">dışı Döndürülen arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8de2d-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8de2d-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8de2d-115">Return Value</span></span>  

 <span data-ttu-id="8de2d-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8de2d-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de2d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8de2d-117">Requirements</span></span>  

 <span data-ttu-id="8de2d-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8de2d-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de2d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8de2d-119">See also</span></span>

- [<span data-ttu-id="8de2d-120">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8de2d-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
