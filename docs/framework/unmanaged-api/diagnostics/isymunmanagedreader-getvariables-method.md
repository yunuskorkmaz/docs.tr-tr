---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetVariables Yöntemi'
title: ISymUnmanagedReader::GetVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: 93208e6c5c65c4c770c533b7ea72de513451d97d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763910"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="4f55e-103">ISymUnmanagedReader::GetVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f55e-103">ISymUnmanagedReader::GetVariables Method</span></span>

<span data-ttu-id="4f55e-104">Üst ve adı verilen yerel olmayan bir değişken döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f55e-104">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f55e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f55e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f55e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f55e-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="4f55e-107">'ndaki Değişkenin üst öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f55e-107">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="4f55e-108">'ndaki `pVars` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="4f55e-108">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="4f55e-109">dışı Değişkenine döndürülen değişken sayısını alan bir işaretçi `pVars` .</span><span class="sxs-lookup"><span data-stu-id="4f55e-109">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="4f55e-110">dışı Değişkenleri alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4f55e-110">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f55e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4f55e-111">Return Value</span></span>  

 <span data-ttu-id="4f55e-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4f55e-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f55e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f55e-113">Requirements</span></span>  

 <span data-ttu-id="4f55e-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4f55e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f55e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f55e-115">See also</span></span>

- [<span data-ttu-id="4f55e-116">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f55e-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
