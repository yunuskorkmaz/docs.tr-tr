---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedwriter:: SetSymAttribute yöntemi'
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
ms.openlocfilehash: 0509e6430646fa67112b29d30d5053eb4a541415
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761999"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="0da3a-103">ISymUnmanagedWriter::SetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0da3a-103">ISymUnmanagedWriter::SetSymAttribute Method</span></span>

<span data-ttu-id="0da3a-104">Özel bir özniteliği adına göre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0da3a-104">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="0da3a-105">Bu öznitelikler, meta veri özel özniteliklerinin aksine sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="0da3a-105">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da3a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0da3a-106">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0da3a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0da3a-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="0da3a-108">'ndaki Özniteliğin tanımlandığı meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0da3a-108">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="0da3a-109">'ndaki `WCHAR` Özniteliği adını içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0da3a-109">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="0da3a-110">'ndaki `ULONG32` Dizi boyutunu belirten bir `data` .</span><span class="sxs-lookup"><span data-stu-id="0da3a-110">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="0da3a-111">'ndaki Öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="0da3a-111">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0da3a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0da3a-112">Return Value</span></span>  

 <span data-ttu-id="0da3a-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0da3a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0da3a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0da3a-114">Requirements</span></span>  

 <span data-ttu-id="0da3a-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0da3a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da3a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0da3a-116">See also</span></span>

- [<span data-ttu-id="0da3a-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0da3a-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
