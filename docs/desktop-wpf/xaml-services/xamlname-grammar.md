---
title: XamlName Dilbilgisi
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: ceb027938b6d4313babbe02949e0b6dd5ee85589
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556700"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="8e95c-102">XamlName Dilbilgisi</span><span class="sxs-lookup"><span data-stu-id="8e95c-102">XamlName Grammar</span></span>

<span data-ttu-id="8e95c-103">XamlName dilbilgisi, daha kolay bir şekilde yeniden oluşturulduğu XAML dil belirtimi [MS-XAML] içinde tanımlanan belirli bir dildilidir.</span><span class="sxs-lookup"><span data-stu-id="8e95c-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="8e95c-104">XAML belirtiminden</span><span class="sxs-lookup"><span data-stu-id="8e95c-104">From the XAML Specification</span></span>

<span data-ttu-id="8e95c-105">[MS-XAML] belirtimi, türler ve özellikler için kullanılan yasal sembolik tanımlayıcılar kümesini tanımlamak için XamlName adlı dilbilgisi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e95c-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="8e95c-106">XamlName türünde dize değerleri aşağıdaki dilbilgisinde uyumlu olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8e95c-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="8e95c-107">Bu, Unicode karakter veritabanında tanımlanan aşağıdaki genel kategori değerlerini kabul eder</span><span class="sxs-lookup"><span data-stu-id="8e95c-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="8e95c-108">Unicode kategorisi</span><span class="sxs-lookup"><span data-stu-id="8e95c-108">Unicode category</span></span>   | <span data-ttu-id="8e95c-109">Description</span><span class="sxs-lookup"><span data-stu-id="8e95c-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="8e95c-110">Lu</span><span class="sxs-lookup"><span data-stu-id="8e95c-110">Lu</span></span>                 | <span data-ttu-id="8e95c-111">Harf, Büyük Harf</span><span class="sxs-lookup"><span data-stu-id="8e95c-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="8e95c-112">Ll</span><span class="sxs-lookup"><span data-stu-id="8e95c-112">Ll</span></span>                 | <span data-ttu-id="8e95c-113">Harf, Küçük Harf</span><span class="sxs-lookup"><span data-stu-id="8e95c-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="8e95c-114">Lt</span><span class="sxs-lookup"><span data-stu-id="8e95c-114">Lt</span></span>                 | <span data-ttu-id="8e95c-115">Harf, Başlık Düzeni</span><span class="sxs-lookup"><span data-stu-id="8e95c-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="8e95c-116">Lm</span><span class="sxs-lookup"><span data-stu-id="8e95c-116">Lm</span></span>                 | <span data-ttu-id="8e95c-117">Harf, Değiştirici</span><span class="sxs-lookup"><span data-stu-id="8e95c-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="8e95c-118">Lo</span><span class="sxs-lookup"><span data-stu-id="8e95c-118">Lo</span></span>                 | <span data-ttu-id="8e95c-119">Harf, Diğer</span><span class="sxs-lookup"><span data-stu-id="8e95c-119">Letter, Other</span></span>                 |
| <span data-ttu-id="8e95c-120">Sütun</span><span class="sxs-lookup"><span data-stu-id="8e95c-120">Mn</span></span>                 | <span data-ttu-id="8e95c-121">İşaret, Aralık dışı</span><span class="sxs-lookup"><span data-stu-id="8e95c-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="8e95c-122">Mc</span><span class="sxs-lookup"><span data-stu-id="8e95c-122">Mc</span></span>                 | <span data-ttu-id="8e95c-123">İşaret, Boşluklu Birleşik</span><span class="sxs-lookup"><span data-stu-id="8e95c-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="8e95c-124">Nd</span><span class="sxs-lookup"><span data-stu-id="8e95c-124">Nd</span></span>                 | <span data-ttu-id="8e95c-125">Sayı, ondalık</span><span class="sxs-lookup"><span data-stu-id="8e95c-125">Number, Decimal</span></span>               |
| <span data-ttu-id="8e95c-126">Nl</span><span class="sxs-lookup"><span data-stu-id="8e95c-126">Nl</span></span>                 | <span data-ttu-id="8e95c-127">Sayı, Harf</span><span class="sxs-lookup"><span data-stu-id="8e95c-127">Number, Letter</span></span>                |

<span data-ttu-id="8e95c-128">XAML, özellik ve olay nitelikli başvurular ve ayrıca ekli Üyeler için kullanılan ikinci bir dilbilgisini, DottedXamlName öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e95c-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="8e95c-129">Daha fazla bilgi için bkz <xref:System.Windows.DependencyProperty> . ve [xaml 'ye Genel Bakış (WPF)](../fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="8e95c-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="8e95c-130">DottedXamlName türünde dize değerleri aşağıdaki dilbilgisinde uyumlu olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8e95c-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="8e95c-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e95c-131">Remarks</span></span>

<span data-ttu-id="8e95c-132">Tam belirtim için bkz. [ \[ MS-xaml \] ](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="8e95c-132">For the complete specification, see [\[MS-XAML\]](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
