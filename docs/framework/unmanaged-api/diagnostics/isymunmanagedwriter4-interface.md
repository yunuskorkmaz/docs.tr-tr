---
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 21d6520aae1367368973da1692f6bca3aeb2c129
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493662"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="56f4a-102">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56f4a-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="56f4a-103">ISymUnmanagedWriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="56f4a-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56f4a-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="56f4a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="56f4a-105">Methods</span></span>  
 <span data-ttu-id="56f4a-106">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="56f4a-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="56f4a-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="56f4a-107">Method</span></span>|<span data-ttu-id="56f4a-108">Description</span><span class="sxs-lookup"><span data-stu-id="56f4a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56f4a-109">GetDebugInfoWithPadding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56f4a-109">GetDebugInfoWithPadding Method</span></span>](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="56f4a-110">Dize verilerini sabit boyutlu hale getirmek için, bir yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="56f4a-110">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="56f4a-111">Yalnızca yol dize uzunluğu değerinden küçükse doldurma verilir `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="56f4a-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="56f4a-112">Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="56f4a-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56f4a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56f4a-113">Requirements</span></span>  
 <span data-ttu-id="56f4a-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="56f4a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f4a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56f4a-115">See also</span></span>

- [<span data-ttu-id="56f4a-116">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="56f4a-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="56f4a-117">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56f4a-117">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
