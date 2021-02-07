---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetNamespaces Yöntemi'
title: ISymUnmanagedReader::GetNamespaces Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 47f7bff829ca2a52eb95d7d7693a7486301de092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764014"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="4333b-103">ISymUnmanagedReader::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="4333b-103">ISymUnmanagedReader::GetNamespaces Method</span></span>

<span data-ttu-id="4333b-104">Bu sembol deposu içindeki genel kapsamda tanımlanan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="4333b-104">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4333b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4333b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4333b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4333b-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="4333b-107">'ndaki Ad alanları dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="4333b-107">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="4333b-108">dışı Ad alanı listesinin uzunluğunu alan bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4333b-108">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="4333b-109">dışı Ad alanı listesini alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4333b-109">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4333b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4333b-110">Return Value</span></span>  

 <span data-ttu-id="4333b-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4333b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4333b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4333b-112">Requirements</span></span>  

 <span data-ttu-id="4333b-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4333b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4333b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4333b-114">See also</span></span>

- [<span data-ttu-id="4333b-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4333b-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
