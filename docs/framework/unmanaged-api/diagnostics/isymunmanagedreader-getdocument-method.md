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
ms.openlocfilehash: 950fb3b9c51ae2c9470b5aadd31c877d7aa6b6f6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615065"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="40c49-102">ISymUnmanagedReader::GetDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="40c49-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="40c49-103">Bir belge bulur.</span><span class="sxs-lookup"><span data-stu-id="40c49-103">Finds a document.</span></span> <span data-ttu-id="40c49-104">Belge dili, satıcı ve tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40c49-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c49-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="40c49-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c49-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40c49-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="40c49-107">'ndaki Belgeyi tanımlayan URL.</span><span class="sxs-lookup"><span data-stu-id="40c49-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="40c49-108">'ndaki Belge dili.</span><span class="sxs-lookup"><span data-stu-id="40c49-108">[in] The document language.</span></span> <span data-ttu-id="40c49-109">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40c49-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="40c49-110">'ndaki Belge dili için satıcının kimliği.</span><span class="sxs-lookup"><span data-stu-id="40c49-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="40c49-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40c49-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="40c49-112">'ndaki Belge türü.</span><span class="sxs-lookup"><span data-stu-id="40c49-112">[in] The type of the document.</span></span> <span data-ttu-id="40c49-113">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40c49-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="40c49-114">dışı Döndürülen arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="40c49-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40c49-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="40c49-115">Return Value</span></span>  
 <span data-ttu-id="40c49-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="40c49-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c49-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40c49-117">Requirements</span></span>  
 <span data-ttu-id="40c49-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="40c49-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c49-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40c49-119">See also</span></span>

- [<span data-ttu-id="40c49-120">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40c49-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
