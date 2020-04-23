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
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071831"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="3eea4-102">XamlName Dilbilgisi</span><span class="sxs-lookup"><span data-stu-id="3eea4-102">XamlName Grammar</span></span>

<span data-ttu-id="3eea4-103">XamlName Grammar, XAML dil belirtiminde [MS-XAML], burada kolaylık sağlamak için çoğaltılan tanımlanan belirli bir dilbilgisidir.</span><span class="sxs-lookup"><span data-stu-id="3eea4-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="3eea4-104">XAML Belirtiminden</span><span class="sxs-lookup"><span data-stu-id="3eea4-104">From the XAML Specification</span></span>

<span data-ttu-id="3eea4-105">[MS-XAML] belirtimi, türleri ve özellikleri için kullanılan yasal sembolik tanımlayıcılar kümesini tanımlamak için XamlName dilbilgisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3eea4-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="3eea4-106">XamlName türünden olan dize değerleri aşağıdaki dilbilgisine uygun olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3eea4-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="3eea4-107">Unicode Karakter Veritabanında tanımlandığı şekilde aşağıdaki genel kategori değerlerini varsayar</span><span class="sxs-lookup"><span data-stu-id="3eea4-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="3eea4-108">Unicode kategorisi</span><span class="sxs-lookup"><span data-stu-id="3eea4-108">Unicode category</span></span>   | <span data-ttu-id="3eea4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eea4-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="3eea4-110">Lu</span><span class="sxs-lookup"><span data-stu-id="3eea4-110">Lu</span></span>                 | <span data-ttu-id="3eea4-111">Harf, Büyük Harf</span><span class="sxs-lookup"><span data-stu-id="3eea4-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="3eea4-112">Ll</span><span class="sxs-lookup"><span data-stu-id="3eea4-112">Ll</span></span>                 | <span data-ttu-id="3eea4-113">Harf, Küçük Harf</span><span class="sxs-lookup"><span data-stu-id="3eea4-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="3eea4-114">Lt</span><span class="sxs-lookup"><span data-stu-id="3eea4-114">Lt</span></span>                 | <span data-ttu-id="3eea4-115">Harf, Başlık Düzeni</span><span class="sxs-lookup"><span data-stu-id="3eea4-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="3eea4-116">Lm</span><span class="sxs-lookup"><span data-stu-id="3eea4-116">Lm</span></span>                 | <span data-ttu-id="3eea4-117">Harf, Değiştirici</span><span class="sxs-lookup"><span data-stu-id="3eea4-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="3eea4-118">Lo</span><span class="sxs-lookup"><span data-stu-id="3eea4-118">Lo</span></span>                 | <span data-ttu-id="3eea4-119">Harf, Diğer</span><span class="sxs-lookup"><span data-stu-id="3eea4-119">Letter, Other</span></span>                 |
| <span data-ttu-id="3eea4-120">Sütun</span><span class="sxs-lookup"><span data-stu-id="3eea4-120">Mn</span></span>                 | <span data-ttu-id="3eea4-121">İşaretleme, Aralıksız</span><span class="sxs-lookup"><span data-stu-id="3eea4-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="3eea4-122">Mc</span><span class="sxs-lookup"><span data-stu-id="3eea4-122">Mc</span></span>                 | <span data-ttu-id="3eea4-123">İşaret, Boşluklu Birleşik</span><span class="sxs-lookup"><span data-stu-id="3eea4-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="3eea4-124">Nd</span><span class="sxs-lookup"><span data-stu-id="3eea4-124">Nd</span></span>                 | <span data-ttu-id="3eea4-125">Sayı, Ondalık</span><span class="sxs-lookup"><span data-stu-id="3eea4-125">Number, Decimal</span></span>               |
| <span data-ttu-id="3eea4-126">Nl</span><span class="sxs-lookup"><span data-stu-id="3eea4-126">Nl</span></span>                 | <span data-ttu-id="3eea4-127">Sayı, Harf</span><span class="sxs-lookup"><span data-stu-id="3eea4-127">Number, Letter</span></span>                |

<span data-ttu-id="3eea4-128">XAML, özellik ve etkinlik nitelikli başvurular için ve ekli üyeler için kullanılan ikinci bir dilbilgisi olan Noktalı XamlName'yi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3eea4-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="3eea4-129">Daha fazla bilgi <xref:System.Windows.DependencyProperty> için bkz ve [XAML Genel Bakış (WPF)](../fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3eea4-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="3eea4-130">DottedXamlName türünden dize değerleri aşağıdaki dilbilgisine uygun olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3eea4-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="3eea4-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eea4-131">Remarks</span></span>

<span data-ttu-id="3eea4-132">Tam belirtim için [ \[\]MS-XAML'ye](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.</span><span class="sxs-lookup"><span data-stu-id="3eea4-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
