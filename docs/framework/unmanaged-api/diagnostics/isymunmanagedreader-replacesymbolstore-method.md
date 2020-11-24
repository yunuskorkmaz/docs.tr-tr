---
title: ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
ms.openlocfilehash: 3fa94094ad066496cc8a1fc4dd2ccb0ee16b5aac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675847"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="aa950-102">ISymUnmanagedReader::ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa950-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>

<span data-ttu-id="aa950-103">Var olan sembol deposunu bir Delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="aa950-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="aa950-104">Bu yöntem [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) yöntemine benzerdir, ancak verilen Delta bir güncelleştirme yerine tam bir değişiklik olarak hareket eder.</span><span class="sxs-lookup"><span data-stu-id="aa950-104">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa950-105">Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` .</span><span class="sxs-lookup"><span data-stu-id="aa950-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="aa950-106">`filename`Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="aa950-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="aa950-107">`pIStream`Belirtilmişse, mağaza içindeki verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="aa950-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa950-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aa950-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa950-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa950-109">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="aa950-110">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="aa950-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="aa950-111">'ndaki Parametresi için alternatif olarak kullanılan dosya akışı `filename` .</span><span class="sxs-lookup"><span data-stu-id="aa950-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa950-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa950-112">Return Value</span></span>  

 <span data-ttu-id="aa950-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="aa950-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa950-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa950-114">Requirements</span></span>  

 <span data-ttu-id="aa950-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aa950-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa950-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa950-116">See also</span></span>

- [<span data-ttu-id="aa950-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa950-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
