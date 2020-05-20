---
title: ISymUnmanagedWriter::SetSymAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 39b0c065a324f2b3939467901739f995bc9abbad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614766"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="cd10d-102">ISymUnmanagedWriter::SetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd10d-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="cd10d-103">Özel bir özniteliği adına göre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cd10d-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="cd10d-104">Bu öznitelikler, meta veri özel özniteliklerinin aksine sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="cd10d-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd10d-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cd10d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd10d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd10d-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="cd10d-107">'ndaki Özniteliğin tanımlandığı meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="cd10d-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="cd10d-108">'ndaki `WCHAR`Özniteliği adını içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cd10d-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="cd10d-109">'ndaki `ULONG32`Dizi boyutunu belirten bir `data` .</span><span class="sxs-lookup"><span data-stu-id="cd10d-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="cd10d-110">'ndaki Öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="cd10d-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd10d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd10d-111">Return Value</span></span>  
 <span data-ttu-id="cd10d-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cd10d-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd10d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd10d-113">Requirements</span></span>  
 <span data-ttu-id="cd10d-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cd10d-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd10d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd10d-115">See also</span></span>

- [<span data-ttu-id="cd10d-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd10d-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
