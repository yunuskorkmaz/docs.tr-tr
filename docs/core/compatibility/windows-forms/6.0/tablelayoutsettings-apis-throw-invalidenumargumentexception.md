---
title: 'Son değişiklik: bazı TableLayoutSettings özellikleri ınvalıdenumargumentexception oluşturur'
description: Bazı TableLayoutSettings API 'Lerinin artık geçersiz bağımsız değişkenler için bir ınvalıdenumargumentexception oluşturandan sonra .NET 6,0 ' deki önemli değişiklik hakkında bilgi edinin.
ms.date: 01/18/2021
ms.openlocfilehash: 8397952e4647347718f11597a100c5d764e7186b
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570277"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a><span data-ttu-id="cc48e-103">Seçili TableLayoutSettings özellikleri throw ınvalıdenumargumentexception</span><span class="sxs-lookup"><span data-stu-id="cc48e-103">Selected TableLayoutSettings properties throw InvalidEnumArgumentException</span></span>

<span data-ttu-id="cc48e-104">Seçili <xref:System.Windows.Forms.TableLayoutSettings> Özellikler artık <xref:System.ComponentModel.InvalidEnumArgumentException> yanlış bir değer atamaya çalışırsanız bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc48e-104">Selected <xref:System.Windows.Forms.TableLayoutSettings> properties now throw an <xref:System.ComponentModel.InvalidEnumArgumentException> if you attempt to assign an incorrect value.</span></span>

## <a name="change-description"></a><span data-ttu-id="cc48e-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="cc48e-105">Change description</span></span>

<span data-ttu-id="cc48e-106">Önceki .NET sürümlerinde, <xref:System.ArgumentOutOfRangeException> yanlış bir değer atamaya çalışırsanız bu özellikler bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc48e-106">In previous .NET versions, these properties throw an <xref:System.ArgumentOutOfRangeException> if you attempt to assign an incorrect value.</span></span> <span data-ttu-id="cc48e-107">.NET 6,0 ' den itibaren bu özellikler bu <xref:System.ComponentModel.InvalidEnumArgumentException> tür durumlarda bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc48e-107">Starting in .NET 6.0, these properties throw an <xref:System.ComponentModel.InvalidEnumArgumentException> in such cases.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="cc48e-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="cc48e-108">Reason for change</span></span>

<span data-ttu-id="cc48e-109"><xref:System.ComponentModel.InvalidEnumArgumentException>, Benzer durumlarda mevcut Windows Forms API 'si ile birlikte oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="cc48e-109">Throwing <xref:System.ComponentModel.InvalidEnumArgumentException> is in line with the existing Windows Forms API in similar situations.</span></span> <span data-ttu-id="cc48e-110">Bu özel durum, geliştiriciler için daha iyi bir hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc48e-110">Throwing this exception also provides developers with a better debug experience.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="cc48e-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="cc48e-111">Version introduced</span></span>

<span data-ttu-id="cc48e-112">.NET 6,0</span><span class="sxs-lookup"><span data-stu-id="cc48e-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="cc48e-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cc48e-113">Recommended action</span></span>

- <span data-ttu-id="cc48e-114">Yanlış değerlerin atanmasını engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="cc48e-114">Update the code to prevent assigning incorrect values.</span></span>
- <span data-ttu-id="cc48e-115">Gerekirse, <xref:System.ComponentModel.InvalidEnumArgumentException> Bu API 'lere erişirken bir işleme işleyin.</span><span class="sxs-lookup"><span data-stu-id="cc48e-115">If necessary, handle an <xref:System.ComponentModel.InvalidEnumArgumentException> when accessing these APIs.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="cc48e-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cc48e-116">Affected APIs</span></span>

<span data-ttu-id="cc48e-117">Aşağıdaki tabloda etkilenen özellikler listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="cc48e-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="cc48e-118">Özellik</span><span class="sxs-lookup"><span data-stu-id="cc48e-118">Property</span></span> | <span data-ttu-id="cc48e-119">Sürüm değişti</span><span class="sxs-lookup"><span data-stu-id="cc48e-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | <span data-ttu-id="cc48e-120">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="cc48e-120">Preview 1</span></span> |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | <span data-ttu-id="cc48e-121">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="cc48e-121">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
