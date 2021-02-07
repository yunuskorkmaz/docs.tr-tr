---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedconstant:: GetName Yöntemi'
title: ISymUnmanagedConstant::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 57531711ed60c9e35e749a3cb1f1ba5d5c48ca66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689826"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="244e2-103">ISymUnmanagedConstant::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="244e2-103">ISymUnmanagedConstant::GetName Method</span></span>

<span data-ttu-id="244e2-104">Sabitin adını alır.</span><span class="sxs-lookup"><span data-stu-id="244e2-104">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="244e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="244e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="244e2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="244e2-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="244e2-107">'ndaki `szName` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="244e2-107">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="244e2-108">dışı `ULONG32` Null sonlandırma dahil olmak üzere, adı içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="244e2-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="244e2-109">dışı Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="244e2-109">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="244e2-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="244e2-110">Return Value</span></span>  

 <span data-ttu-id="244e2-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="244e2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="244e2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="244e2-112">Requirements</span></span>  

 <span data-ttu-id="244e2-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="244e2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244e2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="244e2-114">See also</span></span>

- [<span data-ttu-id="244e2-115">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="244e2-115">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="244e2-116">GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="244e2-116">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="244e2-117">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="244e2-117">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
