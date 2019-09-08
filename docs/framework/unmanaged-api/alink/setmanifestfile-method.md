---
title: SetManifestFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787201"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="36db5-102">SetManifestFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36db5-102">SetManifestFile Method</span></span>
<span data-ttu-id="36db5-103">Bağlayıcının, derlemeyi oluşturduğunda kullandığı bildirim dosyasını belirtmenize veya sıfırlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="36db5-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36db5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36db5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="36db5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36db5-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="36db5-106">İçeriği Win32 kaynakları blobuna yerleştirilen bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="36db5-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36db5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36db5-107">Return Value</span></span>  
 <span data-ttu-id="36db5-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="36db5-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36db5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36db5-109">Remarks</span></span>  
 <span data-ttu-id="36db5-110">Win32ResBlob sorulmadan önce bunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="36db5-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="36db5-111">`pszFile` Parametresinin değeri, içeriği okunan bildirim dosyasının adı ve kimliği RT_MANIFEST olan Win32 kaynaklarına konur.</span><span class="sxs-lookup"><span data-stu-id="36db5-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="36db5-112">NULL parametresi kullanılarak çağrıldığında, daha önce okuma bildirimi temizlenir.</span><span class="sxs-lookup"><span data-stu-id="36db5-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="36db5-113">Bu, bir tane, bağlayıcının durumunu başlatma zamanına sıfırlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="36db5-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36db5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36db5-114">Requirements</span></span>  
 <span data-ttu-id="36db5-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="36db5-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36db5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36db5-116">See also</span></span>

- [<span data-ttu-id="36db5-117">IALink3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36db5-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="36db5-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="36db5-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="36db5-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36db5-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="36db5-120">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="36db5-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
