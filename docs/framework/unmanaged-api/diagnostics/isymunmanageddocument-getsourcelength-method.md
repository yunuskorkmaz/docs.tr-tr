---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: GetSourceLength Yöntemi'
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
ms.openlocfilehash: 91ac1327afc84458c87122dddc31d0f5b2186f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721521"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="12c83-103">ISymUnmanagedDocument::GetSourceLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12c83-103">ISymUnmanagedDocument::GetSourceLength Method</span></span>

<span data-ttu-id="12c83-104">Gömülü kaynağın uzunluğunu bayt olarak alır.</span><span class="sxs-lookup"><span data-stu-id="12c83-104">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c83-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12c83-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12c83-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12c83-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="12c83-107">dışı Gömülü kaynağın bayt cinsinden uzunluğunu belirten bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="12c83-107">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12c83-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="12c83-108">Return Value</span></span>  

 <span data-ttu-id="12c83-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="12c83-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c83-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12c83-110">See also</span></span>

- [<span data-ttu-id="12c83-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12c83-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
