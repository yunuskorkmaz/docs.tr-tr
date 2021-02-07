---
description: 'Daha fazla bilgi edinin: QuotedPairReader Class'
title: QuotedPairReader sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.QuotedPairReader
- System.Net.Mail.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 810a7b02948a1b7aa542a179563af9a6d79dd763
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699668"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="87796-103">QuotedPairReader sınıfı</span><span class="sxs-lookup"><span data-stu-id="87796-103">QuotedPairReader class</span></span>

<span data-ttu-id="87796-104">Tırnak işaretli bir dizede hangi karakterlerin alıntılanmış (kaçışlı) olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="87796-104">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="87796-105">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="87796-105">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="87796-106">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="87796-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="87796-107">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="87796-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="87796-108">CountQuotedChars yöntemi</span><span class="sxs-lookup"><span data-stu-id="87796-108">CountQuotedChars method</span></span>

<span data-ttu-id="87796-109">Belirtilen dizedeki, önceki tırnak içine alınmış birden fazla ters eğik çizgi dahil olmak üzere ardışık olarak tırnak içine alınmış karakterlerin sayısını sayar</span><span class="sxs-lookup"><span data-stu-id="87796-109">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="87796-110">Örneğin, dize `a\\\b` ve bir dizini verildiğinde, tırnak işareti `4` `4` `b` alınır ve bu nedenle önceki üç ters eğik çizgi bulunur.</span><span class="sxs-lookup"><span data-stu-id="87796-110">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="87796-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87796-111">Parameters</span></span>

- <span data-ttu-id="87796-112">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="87796-112">`data` <xref:System.String></span></span>

  <span data-ttu-id="87796-113">Ardışık alıntılanmış karakterlerin sayımının bulunduğu veri dizesi.</span><span class="sxs-lookup"><span data-stu-id="87796-113">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="87796-114">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="87796-114">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="87796-115">Belirtilen dizedeki, ardışık olarak hangi tırnak işaretli karakterlerin sayılmaması gereken konum.</span><span class="sxs-lookup"><span data-stu-id="87796-115">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="87796-116">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="87796-116">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="87796-117">`true` Unicode karakterlerinin atlanmasına izin vermek için; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="87796-117">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="87796-118">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="87796-118">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="87796-119">`0` Belirtilen dizindeki karakter kaçışsız ise; Aksi takdirde, ardışık olarak karakter dahil olmak üzere karakteri de içerecek şekilde ardışık tırnak işareti sayısı `index` .</span><span class="sxs-lookup"><span data-stu-id="87796-119">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="87796-120">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="87796-120">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="87796-121">Atlanan bir Unicode karakteri bulundu, ancak buna izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="87796-121">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="87796-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87796-122">Requirements</span></span>

<span data-ttu-id="87796-123">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="87796-123">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="87796-124">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="87796-124">**Assembly:** System (in System.dll)</span></span>
