---
title: 'Son değişiklik: DataGridView artık özelleştirilmiş hücre stilleri için yazı tiplerini sıfırlıyor'
description: DataGridView 'in, hücre stili yazı tipi özelleştirildiyse, varsayılan hücre stili yazı tiplerini çevresel yazı tipi ile eşleşecek şekilde sıfırlamadiği .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 708b12ba1305681f5c38eb605861d02e3b2c8eb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761720"
---
# <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a><span data-ttu-id="754af-103">DataGridView artık özelleştirilmiş hücre stilleri için yazı tiplerini sıfırlıyor</span><span class="sxs-lookup"><span data-stu-id="754af-103">DataGridView no longer resets fonts for customized cell styles</span></span>

<span data-ttu-id="754af-104">Ortam yazı tipi değiştiğinde, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> hücre stili yazı tipi özelleştirildiyse, varsayılan hücre stili yazı tiplerini artık çevresel yazı tipiyle eşleşecek şekilde sıfırlamamıştır.</span><span class="sxs-lookup"><span data-stu-id="754af-104">When the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> no longer resets default cell style fonts to match the ambient font if the cell style font has been customized.</span></span>

## <a name="change-description"></a><span data-ttu-id="754af-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="754af-105">Change description</span></span>

<span data-ttu-id="754af-106">Önceki .NET sürümlerinde, ortam yazı tipi değişirse <xref:System.Windows.Forms.DataGridViewElement.DataGridView> <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> ,, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> ve özelliklerinde Kullanıcı tanımlı yazı tiplerini sıfırlar ve geçersiz kılar <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="754af-106">In previous .NET versions, if the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> resets and overrides user-defined fonts in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, and <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties.</span></span>

<span data-ttu-id="754af-107">.NET 5,0 ' den başlayarak,, veya özelliklerinde yazı tipi ayarlarını yapılandırırsanız, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> ortam yazı tipi değiştiğinde bile bu ayarlar korunur.</span><span class="sxs-lookup"><span data-stu-id="754af-107">Starting in .NET 5.0, if you configure font settings in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties, those settings are retained even when the ambient font changes.</span></span> <span data-ttu-id="754af-108">Yazı tipini özelleştirmezseniz bu özelliklerden herhangi biri, yazı tipi çevresel yazı tipi ayarlarıyla eşleşecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="754af-108">For any of these properties that you don't customize the font, the font will change to match the ambient font settings.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="754af-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="754af-109">Reason for change</span></span>

<span data-ttu-id="754af-110">[.NET Core 3,0 ' de varsayılan yazı tipi değişikliği](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt)ile, çeşitli hücre stillerinin varsayılan yazı tipi ayarları da değişir.</span><span class="sxs-lookup"><span data-stu-id="754af-110">With the [change of the default font in .NET Core 3.0](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt), the default font settings for the various cell styles also changed.</span></span> <span data-ttu-id="754af-111">Bu davranış, denetimlerinde özel stillendirme <xref:System.Windows.Forms.DataGridViewElement.DataGridView> ve bu uygulamaların .NET Framework ' den .net 5,0 ' e geçişini engelleyen uygulamalar için istenmeyen bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="754af-111">This behavior is undesirable for apps that rely on custom styling in their <xref:System.Windows.Forms.DataGridViewElement.DataGridView> controls, and impeded the migration of these apps from .NET Framework to .NET 5.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="754af-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="754af-112">Version introduced</span></span>

<span data-ttu-id="754af-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="754af-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="754af-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="754af-114">Recommended action</span></span>

<span data-ttu-id="754af-115">Sizin bölüminizdeki herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="754af-115">No action is required on your part.</span></span> <span data-ttu-id="754af-116">Ancak,, veya özelliklerinde yazı tipini özelleştirdiyseniz <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> ve yazı tipinin çevresel yazı tipiyle eşleşmesini istiyorsanız, <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> her bir `null` özellik için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="754af-116">However, if you've customized the font in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties and want the font to match the ambient font, set <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> to `null` for each property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="754af-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="754af-117">Affected APIs</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

### Category

- Windows Forms

-->
