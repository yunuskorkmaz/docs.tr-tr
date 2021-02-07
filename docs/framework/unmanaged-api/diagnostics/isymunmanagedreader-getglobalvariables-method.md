---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetGlobalVariables yöntemi'
title: ISymUnmanagedReader::GetGlobalVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: 2b017d2a5746942f701cf79d3d29f1eb571dceab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689657"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="86136-103">ISymUnmanagedReader::GetGlobalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="86136-103">ISymUnmanagedReader::GetGlobalVariables Method</span></span>

<span data-ttu-id="86136-104">Tüm genel değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="86136-104">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86136-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86136-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86136-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86136-106">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="86136-107">'ndaki Tarafından işaret edilen arabelleğin uzunluğu `pcVars` .</span><span class="sxs-lookup"><span data-stu-id="86136-107">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="86136-108">dışı `ULONG32` Değişkenleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="86136-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="86136-109">dışı Değişkenleri içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="86136-109">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86136-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86136-110">Return Value</span></span>  

 <span data-ttu-id="86136-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="86136-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86136-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86136-112">Requirements</span></span>  

 <span data-ttu-id="86136-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="86136-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86136-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86136-114">See also</span></span>

- [<span data-ttu-id="86136-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86136-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
