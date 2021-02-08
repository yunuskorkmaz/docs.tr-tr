---
description: ': MemoryStream. ınternalgetoriginandlength yöntemi hakkında daha fazla bilgi edinin'
title: MemoryStream. ınternalgetoriginandlength yöntemi (System.IO)
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 4232852c0835a43454f36271a43062e1240297a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802547"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="35665-103">MemoryStream.InternalGetOriginAndLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="35665-103">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="35665-104">Bellek akışının iç başlangıç değerlerini ve uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="35665-104">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="35665-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35665-105">Parameters</span></span>

- <span data-ttu-id="35665-106">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="35665-106">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="35665-107">Bu yöntem döndüğünde, yeni bir nesne oluşturulurken belirtilen bayt dizisinin boşluğu <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="35665-107">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="35665-108">Bayt dizisi tarafından oluşturulduysa 0 içerir <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="35665-108">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="35665-109">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="35665-109">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="35665-110">Bu yöntem döndüğünde, bellek akışı içindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="35665-110">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="35665-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35665-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="35665-112">`MemoryStream.InternalGetOriginAndLength`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="35665-112">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="35665-113">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="35665-113">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="35665-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35665-114">Requirements</span></span>

<span data-ttu-id="35665-115">**Ad alanı:**<xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="35665-115">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="35665-116">**Bütünleştirilmiş kod:** mscorlib.dll (mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="35665-116">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="35665-117">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35665-117">**.NET Framework versions:** Available since 2.0.</span></span>
