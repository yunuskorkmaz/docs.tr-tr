---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetAddressField1 yöntemi'
title: ISymUnmanagedVariable::GetAddressField1 Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: 1ff6862cef52ef8fcb449563198c2df1de356530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763000"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="1232f-103">ISymUnmanagedVariable::GetAddressField1 Metodu</span><span class="sxs-lookup"><span data-stu-id="1232f-103">ISymUnmanagedVariable::GetAddressField1 Method</span></span>

<span data-ttu-id="1232f-104">Bu değişken için ilk adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="1232f-104">Gets the first address field for this variable.</span></span> <span data-ttu-id="1232f-105">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1232f-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1232f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1232f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1232f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1232f-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1232f-108">dışı `ULONG32` İlk adres alanını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1232f-108">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1232f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1232f-109">Return Value</span></span>  

 <span data-ttu-id="1232f-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1232f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1232f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1232f-111">Requirements</span></span>  

 <span data-ttu-id="1232f-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1232f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1232f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1232f-113">See also</span></span>

- [<span data-ttu-id="1232f-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1232f-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="1232f-115">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1232f-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="1232f-116">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1232f-116">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="1232f-117">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1232f-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
