---
title: ISymUnmanagedReader::GetSymAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 763e698c7149de0fee61770e601032a4160b839f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378580"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="64314-102">ISymUnmanagedReader::GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64314-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="64314-103">Özel bir öznitelik adı üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="64314-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="64314-104">Meta veri özel öznitelikleri, bu özel öznitelikler sembol deposu içerisinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="64314-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64314-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64314-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64314-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64314-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="64314-107">[in] Öznitelik istendiği nesnesi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="64314-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="64314-108">[in] Bir işaretçi değişkenine almak için bir özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="64314-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="64314-109">[in] Boyutu `buffer` dizisi.</span><span class="sxs-lookup"><span data-stu-id="64314-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="64314-110">[out] Bir işaretçi değişkenine özniteliği veri uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="64314-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="64314-111">[out] Bir işaretçi değişkenine öznitelik verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="64314-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64314-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64314-112">Return Value</span></span>  
 <span data-ttu-id="64314-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="64314-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64314-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64314-114">Requirements</span></span>  
 <span data-ttu-id="64314-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="64314-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64314-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64314-116">See also</span></span>
- [<span data-ttu-id="64314-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64314-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
