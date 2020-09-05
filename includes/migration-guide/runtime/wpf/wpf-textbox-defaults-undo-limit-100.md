---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497036"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="17c63-101">WPF metin kutusu varsayılan olarak 100 limitini geri alır</span><span class="sxs-lookup"><span data-stu-id="17c63-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="17c63-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="17c63-102">Details</span></span>

<span data-ttu-id="17c63-103">.NET Framework 4,5 ' de, WPF metin kutusu için varsayılan geri alma sınırı 100 ' dir (.NET Framework 4,0 ' de sınırsız olacak şekilde)</span><span class="sxs-lookup"><span data-stu-id="17c63-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="17c63-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="17c63-104">Suggestion</span></span>

<span data-ttu-id="17c63-105">100 'nin bir geri alma sınırı çok düşükse, sınır şu şekilde açık şekilde ayarlanabilir <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="17c63-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="17c63-106">Name</span><span class="sxs-lookup"><span data-stu-id="17c63-106">Name</span></span>    | <span data-ttu-id="17c63-107">Değer</span><span class="sxs-lookup"><span data-stu-id="17c63-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="17c63-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="17c63-108">Scope</span></span>   |<span data-ttu-id="17c63-109">Edge</span><span class="sxs-lookup"><span data-stu-id="17c63-109">Edge</span></span>|
|<span data-ttu-id="17c63-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="17c63-110">Version</span></span>|<span data-ttu-id="17c63-111">4,5</span><span class="sxs-lookup"><span data-stu-id="17c63-111">4.5</span></span>|
|<span data-ttu-id="17c63-112">Tür</span><span class="sxs-lookup"><span data-stu-id="17c63-112">Type</span></span>|<span data-ttu-id="17c63-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="17c63-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="17c63-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="17c63-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
