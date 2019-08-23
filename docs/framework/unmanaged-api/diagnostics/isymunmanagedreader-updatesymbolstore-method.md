---
title: ISymUnmanagedReader::UpdateSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939001"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="f769b-102">ISymUnmanagedReader::UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f769b-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="f769b-103">Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f769b-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="f769b-104">Bu yöntem, sembol deposunu değişimleri ile orijinal taşınabilir yürütülebilir (PE) dosyası eşleşecek şekilde güncelleştirmek için Düzenle ve devam et senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f769b-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f769b-105">`filename` Ya`pIStream` da parametrelerinden yalnızca birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f769b-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="f769b-106">`filename` Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f769b-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="f769b-107">Belirtilmişse, mağaza <xref:System.Runtime.InteropServices.ComTypes.IStream>içindeki verilerle güncelleştirilir. `pIStream`</span><span class="sxs-lookup"><span data-stu-id="f769b-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f769b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f769b-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f769b-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f769b-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="f769b-110">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="f769b-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="f769b-111">'ndaki `filename` Parametresi için alternatif olarak kullanılan dosya akışı.</span><span class="sxs-lookup"><span data-stu-id="f769b-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f769b-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f769b-112">Return Value</span></span>  
 <span data-ttu-id="f769b-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAıL veya diğer bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f769b-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f769b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f769b-114">Requirements</span></span>  
 <span data-ttu-id="f769b-115">**Üst bilgi** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f769b-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f769b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f769b-116">See also</span></span>

- [<span data-ttu-id="f769b-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f769b-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
