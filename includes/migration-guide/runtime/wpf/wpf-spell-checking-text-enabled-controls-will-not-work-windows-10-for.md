---
ms.openlocfilehash: 6d7f998cda6326e1f584713576a0aa27b3a68655
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497128"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="36811-101">Metin özellikli denetimlerde WPF yazım denetimi, işletim sisteminin giriş dili listesinde olmayan diller için Windows 10 ' da çalışmaz</span><span class="sxs-lookup"><span data-stu-id="36811-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="36811-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="36811-102">Details</span></span>

<span data-ttu-id="36811-103">Windows 10 ' da çalışırken, platform yazım denetimi özellikleri yalnızca giriş dilleri listesinde bulunan diller için kullanılabilir olduğundan, yazım denetleyicisi WPF metin özellikli denetimler için çalışmayabilir. Windows 10 ' da, kullanılabilir klavyeler listesine bir dil eklendiğinde, Windows otomatik olarak yazım denetimi özellikleri sağlayan ilgili bir Isteğe bağlı Özellik (FOD) paketini indirir ve yükler.</span><span class="sxs-lookup"><span data-stu-id="36811-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="36811-104">Dili giriş dilleri listesine ekleyerek, yazım denetleyicisi desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="36811-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="36811-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="36811-105">Suggestion</span></span>

<span data-ttu-id="36811-106">Yazım denetimi yapılacak dilin veya metnin, Windows 10 ' da çalışmak üzere yazım denetimi yapmak için bir giriş dili olarak eklenmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="36811-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="36811-107">Name</span><span class="sxs-lookup"><span data-stu-id="36811-107">Name</span></span>    | <span data-ttu-id="36811-108">Değer</span><span class="sxs-lookup"><span data-stu-id="36811-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="36811-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="36811-109">Scope</span></span>   |<span data-ttu-id="36811-110">Edge</span><span class="sxs-lookup"><span data-stu-id="36811-110">Edge</span></span>|
|<span data-ttu-id="36811-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="36811-111">Version</span></span>|<span data-ttu-id="36811-112">4.6</span><span class="sxs-lookup"><span data-stu-id="36811-112">4.6</span></span>|
|<span data-ttu-id="36811-113">Tür</span><span class="sxs-lookup"><span data-stu-id="36811-113">Type</span></span>|<span data-ttu-id="36811-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="36811-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="36811-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="36811-115">Affected APIs</span></span>

<span data-ttu-id="36811-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="36811-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
