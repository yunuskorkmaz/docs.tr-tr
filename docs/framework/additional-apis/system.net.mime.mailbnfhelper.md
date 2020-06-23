---
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
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990371"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="040c6-102">MailBnfHelper sınıfı</span><span class="sxs-lookup"><span data-stu-id="040c6-102">MailBnfHelper class</span></span>

<span data-ttu-id="040c6-103">Internet ileti biçimli dizeleri ayrıştırmak için yardımcı program yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="040c6-103">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="040c6-104">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="040c6-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="040c6-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="040c6-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="040c6-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="040c6-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="040c6-107">Ascii7bitMaxValue alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-107">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="040c6-108">En fazla 7 bit ASCII değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-108">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="040c6-109">Atext alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-109">Atext field</span></span>

<span data-ttu-id="040c6-110">Alar 'da izin verilen karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-110">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="040c6-111">CR alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-111">CR field</span></span>

<span data-ttu-id="040c6-112">Satır başı karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-112">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="040c6-113">Ctext alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-113">Ctext field</span></span>

<span data-ttu-id="040c6-114">Açıklamaların içinde izin verilen karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-114">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="040c6-115">Nokta alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-115">Dot field</span></span>

<span data-ttu-id="040c6-116">Tam durdurma karakterini () temsil eder `.` .</span><span class="sxs-lookup"><span data-stu-id="040c6-116">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="040c6-117">EndComment alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-117">EndComment field</span></span>

<span data-ttu-id="040c6-118">Açıklamanın sonunu belirten karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-118">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="040c6-119">LF alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-119">LF field</span></span>

<span data-ttu-id="040c6-120">Satır besleme karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-120">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="040c6-121">Alan alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-121">Space field</span></span>

<span data-ttu-id="040c6-122">Boşluk karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-122">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="040c6-123">StartComment alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-123">StartComment field</span></span>

<span data-ttu-id="040c6-124">Açıklamanın başlangıcını belirten karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-124">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="040c6-125">Sekme alanı</span><span class="sxs-lookup"><span data-stu-id="040c6-125">Tab field</span></span>

<span data-ttu-id="040c6-126">Sekme karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="040c6-126">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="040c6-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="040c6-127">Requirements</span></span>

<span data-ttu-id="040c6-128">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="040c6-128">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="040c6-129">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="040c6-129">**Assembly:** System (in System.dll)</span></span>
