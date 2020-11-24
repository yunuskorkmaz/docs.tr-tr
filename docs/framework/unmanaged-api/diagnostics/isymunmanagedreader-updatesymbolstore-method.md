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
ms.openlocfilehash: 6670d985eed4c55550b23d3f4110ee20f3b75661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675834"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="3f9d8-102">ISymUnmanagedReader::UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f9d8-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>

<span data-ttu-id="3f9d8-103">Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="3f9d8-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="3f9d8-104">Bu yöntem, sembol deposunu değişimleri ile orijinal taşınabilir yürütülebilir (PE) dosyası eşleşecek şekilde güncelleştirmek için Düzenle ve devam et senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f9d8-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f9d8-105">Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` .</span><span class="sxs-lookup"><span data-stu-id="3f9d8-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="3f9d8-106">`filename`Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f9d8-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="3f9d8-107">`pIStream`Belirtilmişse, mağaza içindeki verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="3f9d8-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9d8-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3f9d8-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f9d8-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f9d8-109">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="3f9d8-110">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3f9d8-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="3f9d8-111">'ndaki Parametresi için alternatif olarak kullanılan dosya akışı `filename` .</span><span class="sxs-lookup"><span data-stu-id="3f9d8-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f9d8-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f9d8-112">Return Value</span></span>  

 <span data-ttu-id="3f9d8-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3f9d8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f9d8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f9d8-114">Requirements</span></span>  

 <span data-ttu-id="3f9d8-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3f9d8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f9d8-116">See also</span></span>

- [<span data-ttu-id="3f9d8-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f9d8-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
