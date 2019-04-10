---
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5732cc08512df25a14cc8ea9dcaa03c56207dde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202052"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="002bd-102">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="002bd-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="002bd-103">Isymunmanagedwriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="002bd-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="002bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="002bd-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="002bd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="002bd-105">Methods</span></span>  
 <span data-ttu-id="002bd-106">Bu arabirimi aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="002bd-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="002bd-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="002bd-107">Method</span></span>|<span data-ttu-id="002bd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="002bd-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="002bd-109">GetDebugInfoWithPadding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002bd-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="002bd-110">Aynı şekilde işler [Getdebugınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) yol dizesi sabit bir boyuta dize verileri yapmak için bir sonlandırıcı null karakteri aşağıdaki sıfırlarla dışında `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="002bd-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="002bd-111">Doldurma yolu dize uzunluğu kendisi ise yalnızca verilen küçüktür `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="002bd-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="002bd-112">Bu araçlar, fark PE dosyaları yazmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="002bd-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="002bd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="002bd-113">Requirements</span></span>  
 <span data-ttu-id="002bd-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="002bd-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002bd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="002bd-115">See also</span></span>

- [<span data-ttu-id="002bd-116">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="002bd-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="002bd-117">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="002bd-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
