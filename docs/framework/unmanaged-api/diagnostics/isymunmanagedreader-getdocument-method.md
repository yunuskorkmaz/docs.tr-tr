---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetDocument yöntemi'
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
ms.openlocfilehash: 7f2f31467cfd00de68737224a2c1af5b1e78efed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764105"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="eb2fc-103">ISymUnmanagedReader::GetDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="eb2fc-103">ISymUnmanagedReader::GetDocument Method</span></span>

<span data-ttu-id="eb2fc-104">Bir belge bulur.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-104">Finds a document.</span></span> <span data-ttu-id="eb2fc-105">Belge dili, satıcı ve tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-105">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2fc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb2fc-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb2fc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb2fc-107">Parameters</span></span>  

 `url`  
 <span data-ttu-id="eb2fc-108">'ndaki Belgeyi tanımlayan URL.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-108">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="eb2fc-109">'ndaki Belge dili.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-109">[in] The document language.</span></span> <span data-ttu-id="eb2fc-110">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-110">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="eb2fc-111">'ndaki Belge dili için satıcının kimliği.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-111">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="eb2fc-112">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-112">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="eb2fc-113">'ndaki Belge türü.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-113">[in] The type of the document.</span></span> <span data-ttu-id="eb2fc-114">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-114">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="eb2fc-115">dışı Döndürülen arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-115">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb2fc-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eb2fc-116">Return Value</span></span>  

 <span data-ttu-id="eb2fc-117">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2fc-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb2fc-118">Requirements</span></span>  

 <span data-ttu-id="eb2fc-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eb2fc-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2fc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb2fc-120">See also</span></span>

- [<span data-ttu-id="eb2fc-121">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb2fc-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
