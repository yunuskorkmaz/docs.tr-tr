---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 4ac2cccfb17d82d8c62ad7db89161aa794825ae5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678283"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="590ab-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu</span><span class="sxs-lookup"><span data-stu-id="590ab-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>

<span data-ttu-id="590ab-103">Dize verilerini sabit boyutlu hale getirmek için, bir yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="590ab-103">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="590ab-104">Yalnızca yol dize uzunluğu değerinden küçükse doldurma verilir `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="590ab-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="590ab-105">Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="590ab-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="590ab-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="590ab-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="590ab-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="590ab-107">Parameters</span></span>  
  
|<span data-ttu-id="590ab-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="590ab-108">Parameter</span></span>|<span data-ttu-id="590ab-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="590ab-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="590ab-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="590ab-110">Return Value</span></span>  

 <span data-ttu-id="590ab-111">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="590ab-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="590ab-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="590ab-112">Requirements</span></span>  

 <span data-ttu-id="590ab-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="590ab-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590ab-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="590ab-114">See also</span></span>

- [<span data-ttu-id="590ab-115">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="590ab-115">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
