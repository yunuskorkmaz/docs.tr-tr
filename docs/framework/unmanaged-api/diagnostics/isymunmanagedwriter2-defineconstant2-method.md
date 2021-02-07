---
description: 'Hakkında daha fazla bilgi edinin: ISymUnmanagedWriter2::D efineConstant2 yöntemi'
title: ISymUnmanagedWriter2::DefineConstant2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 9a0c444909055e18bdcd0b54fefbc8534ff8681e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761934"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="b8997-103">ISymUnmanagedWriter2::DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8997-103">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>

<span data-ttu-id="b8997-104">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8997-104">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8997-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8997-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8997-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8997-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="b8997-107">'ndaki Sabit adı.</span><span class="sxs-lookup"><span data-stu-id="b8997-107">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="b8997-108">'ndaki Sabitin değeri.</span><span class="sxs-lookup"><span data-stu-id="b8997-108">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="b8997-109">'ndaki Sabitin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="b8997-109">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8997-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b8997-110">Return Value</span></span>  

 <span data-ttu-id="b8997-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b8997-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8997-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8997-112">Requirements</span></span>  

 <span data-ttu-id="b8997-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b8997-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8997-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8997-114">See also</span></span>

- [<span data-ttu-id="b8997-115">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8997-115">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="b8997-116">DefineConstant Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8997-116">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
