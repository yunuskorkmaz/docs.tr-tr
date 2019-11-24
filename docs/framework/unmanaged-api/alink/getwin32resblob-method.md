---
title: GetWin32ResBlob Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: ff3103a46390c880a56ff443bfe20744f2ba0bfd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430692"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="c1a90-102">GetWin32ResBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="c1a90-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="c1a90-103">Retrieves Win32 resource blob.</span><span class="sxs-lookup"><span data-stu-id="c1a90-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="c1a90-104">Call this method after setting assembly options.</span><span class="sxs-lookup"><span data-stu-id="c1a90-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a90-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1a90-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1a90-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1a90-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c1a90-107">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="c1a90-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c1a90-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span><span class="sxs-lookup"><span data-stu-id="c1a90-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="c1a90-109">TRUE if file is a DLL, false for an EXE.</span><span class="sxs-lookup"><span data-stu-id="c1a90-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="c1a90-110">Optional icon to insert into the resource blob.</span><span class="sxs-lookup"><span data-stu-id="c1a90-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="c1a90-111">Receives the resource blob.</span><span class="sxs-lookup"><span data-stu-id="c1a90-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="c1a90-112">Receives the size of the blob.</span><span class="sxs-lookup"><span data-stu-id="c1a90-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1a90-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1a90-113">Return Value</span></span>  
 <span data-ttu-id="c1a90-114">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="c1a90-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a90-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1a90-115">Requirements</span></span>  
 <span data-ttu-id="c1a90-116">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="c1a90-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a90-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a90-117">See also</span></span>

- [<span data-ttu-id="c1a90-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a90-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c1a90-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a90-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c1a90-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="c1a90-120">ALink API</span></span>](index.md)
