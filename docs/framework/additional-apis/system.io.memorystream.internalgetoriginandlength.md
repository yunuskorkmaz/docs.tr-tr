---
title: MemoryStream. ınternalgetoriginandlength yöntemi (System.IO)
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284033"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="bfe79-102">MemoryStream. ınternalgetoriginandlength yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfe79-102">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="bfe79-103">Bellek akışının iç başlangıç değerlerini ve uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="bfe79-103">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="bfe79-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfe79-104">Parameters</span></span>

- <span data-ttu-id="bfe79-105">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="bfe79-105">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="bfe79-106">Bu yöntem, yeni bir <xref:System.IO.MemoryStream> nesnesi oluşturulurken belirtilen bayt dizisinin sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bfe79-106">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="bfe79-107">Bayt dizisi <xref:System.IO.MemoryStream>tarafından oluşturulduysa 0 içerir.</span><span class="sxs-lookup"><span data-stu-id="bfe79-107">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="bfe79-108">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="bfe79-108">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="bfe79-109">Bu yöntem döndüğünde, bellek akışı içindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="bfe79-109">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfe79-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfe79-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="bfe79-111">`MemoryStream.InternalGetOriginAndLength` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bfe79-111">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bfe79-112">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bfe79-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfe79-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfe79-113">Requirements</span></span>

<span data-ttu-id="bfe79-114">**Ad alanı:** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="bfe79-114">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="bfe79-115">**Bütünleştirilmiş kod:** mscorlib. dll (mscorlib. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="bfe79-115">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="bfe79-116">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bfe79-116">**.NET Framework versions:** Available since 2.0.</span></span>
