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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b26f08548ac964fae2f4d64db50167add327eb2d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777361"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="4ca28-102">GetWin32ResBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="4ca28-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="4ca28-103">Win32 kaynak blobu alır.</span><span class="sxs-lookup"><span data-stu-id="4ca28-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="4ca28-104">Derleme seçeneklerini ayarladıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="4ca28-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca28-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ca28-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4ca28-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ca28-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4ca28-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4ca28-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4ca28-108">Win32 sürüm kaynağı oluşturulurken kullanılacak dosya adını almak için kullanılan dosya belirteci</span><span class="sxs-lookup"><span data-stu-id="4ca28-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="4ca28-109">Dosya DLL ise TRUE, bir EXE için false.</span><span class="sxs-lookup"><span data-stu-id="4ca28-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="4ca28-110">Kaynak blobuna eklenecek isteğe bağlı simge.</span><span class="sxs-lookup"><span data-stu-id="4ca28-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="4ca28-111">Kaynak blobu alır.</span><span class="sxs-lookup"><span data-stu-id="4ca28-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="4ca28-112">Blobun boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="4ca28-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ca28-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4ca28-113">Return Value</span></span>  
 <span data-ttu-id="4ca28-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ca28-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ca28-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ca28-115">Requirements</span></span>  
 <span data-ttu-id="4ca28-116">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="4ca28-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca28-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ca28-117">See also</span></span>

- [<span data-ttu-id="4ca28-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ca28-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4ca28-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ca28-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4ca28-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="4ca28-120">ALink API</span></span>](index.md)
