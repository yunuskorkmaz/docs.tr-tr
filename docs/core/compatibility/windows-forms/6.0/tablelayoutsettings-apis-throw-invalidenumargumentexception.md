---
title: 'Son değişiklik: bazı TableLayoutSettings özellikleri ınvalıdenumargumentexception oluşturur'
description: .NET 6 ' daki Son değişiklik hakkında bilgi edinmek için bazı TableLayoutSettings API 'Lerinin artık geçersiz bağımsız değişkenler için bir ınvalıdenumargumentexception oluşturması.
ms.date: 01/18/2021
ms.openlocfilehash: 2da097122b935ec3a60c2bb009cc8ebbcff6468e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255730"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a><span data-ttu-id="71941-103">Seçili TableLayoutSettings özellikleri throw ınvalıdenumargumentexception</span><span class="sxs-lookup"><span data-stu-id="71941-103">Selected TableLayoutSettings properties throw InvalidEnumArgumentException</span></span>

<span data-ttu-id="71941-104">Seçili <xref:System.Windows.Forms.TableLayoutSettings> Özellikler artık <xref:System.ComponentModel.InvalidEnumArgumentException> yanlış bir değer atamaya çalışırsanız bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71941-104">Selected <xref:System.Windows.Forms.TableLayoutSettings> properties now throw an <xref:System.ComponentModel.InvalidEnumArgumentException> if you attempt to assign an incorrect value.</span></span>

## <a name="change-description"></a><span data-ttu-id="71941-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="71941-105">Change description</span></span>

<span data-ttu-id="71941-106">Önceki .NET sürümlerinde, <xref:System.ArgumentOutOfRangeException> yanlış bir değer atamaya çalışırsanız bu özellikler bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71941-106">In previous .NET versions, these properties throw an <xref:System.ArgumentOutOfRangeException> if you attempt to assign an incorrect value.</span></span> <span data-ttu-id="71941-107">.NET 6 ' dan itibaren, bu özellikler bu <xref:System.ComponentModel.InvalidEnumArgumentException> gibi durumlarda oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71941-107">Starting in .NET 6, these properties throw an <xref:System.ComponentModel.InvalidEnumArgumentException> in such cases.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="71941-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="71941-108">Reason for change</span></span>

<span data-ttu-id="71941-109"><xref:System.ComponentModel.InvalidEnumArgumentException>, Benzer durumlarda mevcut Windows Forms API 'si ile birlikte oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="71941-109">Throwing <xref:System.ComponentModel.InvalidEnumArgumentException> is in line with the existing Windows Forms API in similar situations.</span></span> <span data-ttu-id="71941-110">Bu özel durum, geliştiriciler için daha iyi bir hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="71941-110">Throwing this exception also provides developers with a better debug experience.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="71941-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="71941-111">Version introduced</span></span>

<span data-ttu-id="71941-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="71941-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="71941-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="71941-113">Recommended action</span></span>

- <span data-ttu-id="71941-114">Yanlış değerlerin atanmasını engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="71941-114">Update the code to prevent assigning incorrect values.</span></span>
- <span data-ttu-id="71941-115">Gerekirse, <xref:System.ComponentModel.InvalidEnumArgumentException> Bu API 'lere erişirken bir işleme işleyin.</span><span class="sxs-lookup"><span data-stu-id="71941-115">If necessary, handle an <xref:System.ComponentModel.InvalidEnumArgumentException> when accessing these APIs.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="71941-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="71941-116">Affected APIs</span></span>

<span data-ttu-id="71941-117">Aşağıdaki tabloda etkilenen özellikler listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="71941-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="71941-118">Özellik</span><span class="sxs-lookup"><span data-stu-id="71941-118">Property</span></span> | <span data-ttu-id="71941-119">Sürüm değişti</span><span class="sxs-lookup"><span data-stu-id="71941-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | <span data-ttu-id="71941-120">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="71941-120">Preview 1</span></span> |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | <span data-ttu-id="71941-121">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="71941-121">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
