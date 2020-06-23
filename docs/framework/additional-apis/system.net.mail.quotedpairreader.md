---
title: QuotedPairReader sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990372"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="3b94e-102">QuotedPairReader sınıfı</span><span class="sxs-lookup"><span data-stu-id="3b94e-102">QuotedPairReader class</span></span>

<span data-ttu-id="3b94e-103">Tırnak işaretli bir dizede hangi karakterlerin alıntılanmış (kaçışlı) olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="3b94e-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="3b94e-104">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="3b94e-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="3b94e-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b94e-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="3b94e-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3b94e-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="3b94e-107">CountQuotedChars yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b94e-107">CountQuotedChars method</span></span>

<span data-ttu-id="3b94e-108">Belirtilen dizedeki, önceki tırnak içine alınmış birden fazla ters eğik çizgi dahil olmak üzere ardışık olarak tırnak içine alınmış karakterlerin sayısını sayar</span><span class="sxs-lookup"><span data-stu-id="3b94e-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="3b94e-109">Örneğin, dize `a\\\b` ve bir dizini verildiğinde, tırnak işareti `4` `4` `b` alınır ve bu nedenle önceki üç ters eğik çizgi bulunur.</span><span class="sxs-lookup"><span data-stu-id="3b94e-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="3b94e-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b94e-110">Parameters</span></span>

- <span data-ttu-id="3b94e-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="3b94e-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="3b94e-112">Ardışık alıntılanmış karakterlerin sayımının bulunduğu veri dizesi.</span><span class="sxs-lookup"><span data-stu-id="3b94e-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="3b94e-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="3b94e-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="3b94e-114">Belirtilen dizedeki, ardışık olarak hangi tırnak işaretli karakterlerin sayılmaması gereken konum.</span><span class="sxs-lookup"><span data-stu-id="3b94e-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="3b94e-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="3b94e-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="3b94e-116">`true`Unicode karakterlerinin atlanmasına izin vermek için; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="3b94e-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="3b94e-117">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="3b94e-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="3b94e-118">`0`Belirtilen dizindeki karakter kaçışsız ise; Aksi takdirde, ardışık olarak karakter dahil olmak üzere karakteri de içerecek şekilde ardışık tırnak işareti sayısı `index` .</span><span class="sxs-lookup"><span data-stu-id="3b94e-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="3b94e-119">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="3b94e-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="3b94e-120">Atlanan bir Unicode karakteri bulundu, ancak buna izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="3b94e-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b94e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b94e-121">Requirements</span></span>

<span data-ttu-id="3b94e-122">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="3b94e-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="3b94e-123">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="3b94e-123">**Assembly:** System (in System.dll)</span></span>
