---
description: 'Daha fazla bilgi edinin: ISymUnmanagedReader2:: GetSymAttributePreRemap yöntemi'
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
ms.openlocfilehash: 843a3d2d2a568fdff83d2e416fff426daad14645
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763637"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="4de93-103">ISymUnmanagedReader2::GetSymAttributePreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="4de93-103">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>

<span data-ttu-id="4de93-104">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="4de93-104">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="4de93-105">Meta veri özel özniteliklerinin aksine, bu öznitelikler sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="4de93-105">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4de93-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4de93-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4de93-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4de93-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="4de93-108">'ndaki Üst öğenin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4de93-108">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="4de93-109">'ndaki Adını içeren bir işaretçisi `WCHAR` .</span><span class="sxs-lookup"><span data-stu-id="4de93-109">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="4de93-110">'ndaki `ULONG32` Dizi boyutunu belirten bir `buffer` .</span><span class="sxs-lookup"><span data-stu-id="4de93-110">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="4de93-111">dışı `ULONG32` Öznitelik baytlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4de93-111">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4de93-112">dışı Öznitelik baytlarını alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4de93-112">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4de93-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4de93-113">Return Value</span></span>  

 <span data-ttu-id="4de93-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4de93-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4de93-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4de93-115">Requirements</span></span>  

 <span data-ttu-id="4de93-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4de93-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de93-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4de93-117">See also</span></span>

- [<span data-ttu-id="4de93-118">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4de93-118">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
