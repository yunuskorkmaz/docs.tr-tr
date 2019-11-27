---
title: ISymUnmanagedReader2::GetMethodsInDocument Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
ms.openlocfilehash: 70c1d87ae32fb70f8d9f6e32b527394022459526
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446437"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="46526-102">ISymUnmanagedReader2::GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46526-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="46526-103">Belirtilen belgede satır bilgilerine sahip her yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="46526-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46526-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46526-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46526-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46526-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="46526-106">'ndaki Belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46526-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="46526-107">'ndaki `pRetVal` dizisinin boyutunu belirten `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="46526-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="46526-108">dışı Yöntemleri içermesi için gereken arabelleğin boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="46526-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="46526-109">dışı Yöntemleri alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="46526-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46526-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="46526-110">Return Value</span></span>  
 <span data-ttu-id="46526-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="46526-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46526-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46526-112">Requirements</span></span>  
 <span data-ttu-id="46526-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="46526-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46526-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46526-114">See also</span></span>

- [<span data-ttu-id="46526-115">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46526-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
