---
description: 'Hakkında daha fazla bilgi edinin: ıriveconstant yöntemi:D'
title: ISymUnmanagedWriter::DefineConstant Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: 4c3fd3986d42061272406150422f037236c4b9bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762532"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="ecbca-103">ISymUnmanagedWriter::DefineConstant Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecbca-103">ISymUnmanagedWriter::DefineConstant Method</span></span>

<span data-ttu-id="ecbca-104">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ecbca-104">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecbca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecbca-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecbca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecbca-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="ecbca-107">'ndaki `WCHAR` Sabit adı tanımlayan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ecbca-107">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="ecbca-108">'ndaki Sabitin değeri.</span><span class="sxs-lookup"><span data-stu-id="ecbca-108">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="ecbca-109">'ndaki `signature` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ecbca-109">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="ecbca-110">'ndaki Sabit için tür imzası.</span><span class="sxs-lookup"><span data-stu-id="ecbca-110">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecbca-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ecbca-111">Return Value</span></span>  

 <span data-ttu-id="ecbca-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ecbca-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecbca-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecbca-113">Requirements</span></span>  

 <span data-ttu-id="ecbca-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ecbca-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecbca-115">See also</span></span>

- [<span data-ttu-id="ecbca-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecbca-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="ecbca-117">DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecbca-117">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)
