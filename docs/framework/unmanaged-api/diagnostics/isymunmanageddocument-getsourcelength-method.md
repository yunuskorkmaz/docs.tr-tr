---
title: ISymUnmanagedDocument::GetSourceLength Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
ms.openlocfilehash: c384fe6c4357c63bc56f9f9b1cc907dea64fddf7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700944"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="467b2-102">ISymUnmanagedDocument::GetSourceLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="467b2-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>

<span data-ttu-id="467b2-103">Gömülü kaynağın uzunluğunu bayt olarak alır.</span><span class="sxs-lookup"><span data-stu-id="467b2-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467b2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="467b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="467b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="467b2-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="467b2-106">dışı Gömülü kaynağın bayt cinsinden uzunluğunu belirten bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="467b2-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="467b2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="467b2-107">Return Value</span></span>  

 <span data-ttu-id="467b2-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="467b2-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467b2-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="467b2-109">See also</span></span>

- [<span data-ttu-id="467b2-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="467b2-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
