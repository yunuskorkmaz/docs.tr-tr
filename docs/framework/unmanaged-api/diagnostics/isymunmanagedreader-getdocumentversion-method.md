---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetDocumentVersion yöntemi'
title: ISymUnmanagedReader::GetDocumentVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: e6877a10f0c285186330b320c9b614939f4d9e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800207"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="a4a39-103">ISymUnmanagedReader::GetDocumentVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="a4a39-103">ISymUnmanagedReader::GetDocumentVersion Method</span></span>

<span data-ttu-id="a4a39-104">Belirtilen belgenin belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="a4a39-104">Gets the specified version of the specified document.</span></span> <span data-ttu-id="a4a39-105">Belge sürümü 1 ' de başlar ve belge [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) yöntemi kullanılarak her güncelleştirildiği zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="a4a39-105">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="a4a39-106">`pbCurrent`Parametresi ise `true` , bu belgenin en son sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="a4a39-106">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a39-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4a39-107">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4a39-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4a39-108">Parameters</span></span>  

 `pDoc`  
 <span data-ttu-id="a4a39-109">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="a4a39-109">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="a4a39-110">dışı Belirtilen belgenin sürümünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4a39-110">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="a4a39-111">dışı `true` Belgenin en son sürümü ise veya `false` en son sürüm değilse alan bir değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4a39-111">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4a39-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a4a39-112">Return Value</span></span>  

 <span data-ttu-id="a4a39-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a4a39-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4a39-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4a39-114">Requirements</span></span>  

 <span data-ttu-id="a4a39-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a4a39-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a39-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a39-116">See also</span></span>

- [<span data-ttu-id="a4a39-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4a39-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
