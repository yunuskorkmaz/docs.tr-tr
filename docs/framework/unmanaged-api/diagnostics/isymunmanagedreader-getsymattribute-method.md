---
title: ISymUnmanagedReader::GetSymAttribute Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f57d2c4541945d90b1695850311928884fdc9cc5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="445fe-102">ISymUnmanagedReader::GetSymAttribute Metodu</span><span class="sxs-lookup"><span data-stu-id="445fe-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="445fe-103">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="445fe-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="445fe-104">Meta veri özel öznitelikler, bu özel öznitelikler simgesi deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="445fe-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="445fe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="445fe-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="445fe-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="445fe-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="445fe-107">[in] Öznitelik istenen nesnesi için meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="445fe-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="445fe-108">[in] Bir işaretçi değişkenine almak için özniteliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="445fe-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="445fe-109">[in] Boyutunu `buffer` dizi.</span><span class="sxs-lookup"><span data-stu-id="445fe-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="445fe-110">[out] Öznitelik verilerini uzunluğunu alır değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="445fe-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="445fe-111">[out] Öznitelik verileri alan değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="445fe-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="445fe-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="445fe-112">Return Value</span></span>  
 <span data-ttu-id="445fe-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu...</span><span class="sxs-lookup"><span data-stu-id="445fe-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="445fe-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="445fe-114">Requirements</span></span>  
 <span data-ttu-id="445fe-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="445fe-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="445fe-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="445fe-116">See Also</span></span>  
 [<span data-ttu-id="445fe-117">Isymunmanagedreader arabirimi</span><span class="sxs-lookup"><span data-stu-id="445fe-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
