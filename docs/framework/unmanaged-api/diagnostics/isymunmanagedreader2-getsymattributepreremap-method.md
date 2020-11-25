---
title: ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 812c0d08930efff9140c6e897d3f93c4909e8464
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709095"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="ff4bf-102">ISymUnmanagedReader2::GetSymAttributePreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="ff4bf-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>

<span data-ttu-id="ff4bf-103">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="ff4bf-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="ff4bf-104">Meta veri özel özniteliklerinin aksine, bu öznitelikler sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="ff4bf-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4bf-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ff4bf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff4bf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff4bf-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="ff4bf-107">'ndaki Üst öğenin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ff4bf-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="ff4bf-108">'ndaki Adını içeren bir işaretçisi `WCHAR` .</span><span class="sxs-lookup"><span data-stu-id="ff4bf-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="ff4bf-109">'ndaki `ULONG32` Dizi boyutunu belirten bir `buffer` .</span><span class="sxs-lookup"><span data-stu-id="ff4bf-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="ff4bf-110">dışı `ULONG32` Öznitelik baytlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ff4bf-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="ff4bf-111">dışı Öznitelik baytlarını alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ff4bf-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff4bf-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ff4bf-112">Return Value</span></span>  

 <span data-ttu-id="ff4bf-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ff4bf-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff4bf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff4bf-114">Requirements</span></span>  

 <span data-ttu-id="ff4bf-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ff4bf-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4bf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff4bf-116">See also</span></span>

- [<span data-ttu-id="ff4bf-117">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff4bf-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
