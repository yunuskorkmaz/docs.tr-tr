---
description: 'Hakkında daha fazla bilgi edinin: MailBnfHelper sınıfı'
title: MailBnfHelper sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 942b5c423d2f63985a8f7840f69d956bbade7582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699655"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="f9d8e-103">MailBnfHelper sınıfı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-103">MailBnfHelper class</span></span>

<span data-ttu-id="f9d8e-104">Internet ileti biçimli dizeleri ayrıştırmak için yardımcı program yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-104">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="f9d8e-105">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-105">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="f9d8e-106">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f9d8e-107">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="f9d8e-108">Ascii7bitMaxValue alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-108">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="f9d8e-109">En fazla 7 bit ASCII değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-109">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="f9d8e-110">Atext alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-110">Atext field</span></span>

<span data-ttu-id="f9d8e-111">Alar 'da izin verilen karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-111">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="f9d8e-112">CR alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-112">CR field</span></span>

<span data-ttu-id="f9d8e-113">Satır başı karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-113">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="f9d8e-114">Ctext alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-114">Ctext field</span></span>

<span data-ttu-id="f9d8e-115">Açıklamaların içinde izin verilen karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-115">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="f9d8e-116">Nokta alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-116">Dot field</span></span>

<span data-ttu-id="f9d8e-117">Tam durdurma karakterini () temsil eder `.` .</span><span class="sxs-lookup"><span data-stu-id="f9d8e-117">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="f9d8e-118">EndComment alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-118">EndComment field</span></span>

<span data-ttu-id="f9d8e-119">Açıklamanın sonunu belirten karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-119">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="f9d8e-120">LF alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-120">LF field</span></span>

<span data-ttu-id="f9d8e-121">Satır besleme karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-121">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="f9d8e-122">Alan alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-122">Space field</span></span>

<span data-ttu-id="f9d8e-123">Boşluk karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-123">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="f9d8e-124">StartComment alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-124">StartComment field</span></span>

<span data-ttu-id="f9d8e-125">Açıklamanın başlangıcını belirten karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-125">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="f9d8e-126">Sekme alanı</span><span class="sxs-lookup"><span data-stu-id="f9d8e-126">Tab field</span></span>

<span data-ttu-id="f9d8e-127">Sekme karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9d8e-127">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="f9d8e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9d8e-128">Requirements</span></span>

<span data-ttu-id="f9d8e-129">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f9d8e-129">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f9d8e-130">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="f9d8e-130">**Assembly:** System (in System.dll)</span></span>
