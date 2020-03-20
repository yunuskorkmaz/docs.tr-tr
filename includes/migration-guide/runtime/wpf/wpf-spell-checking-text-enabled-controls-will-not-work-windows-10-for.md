---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858653"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="a2fda-101">Metin etkin denetimlerde WPF yazım denetimi, işletim sistemi giriş dil listesinde olmayan diller için Windows 10'da çalışmaz</span><span class="sxs-lookup"><span data-stu-id="a2fda-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a2fda-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a2fda-102">Details</span></span>|<span data-ttu-id="a2fda-103">Windows 10'da çalışırken, platform yazım denetimi yetenekleri yalnızca giriş dilleri listesinde bulunan diller için kullanılabilir olduğundan yazım denetleyicisi WPF metin etkin denetimleri için çalışmayabilir. Windows 10'da, kullanılabilir klavyeler listesine bir dil eklendiğinde, Windows yazım denetimi özellikleri sağlayan ilgili Bir İsteğe Bağlı Özellik (FOD) paketini otomatik olarak karşıdan yükler ve yükler.</span><span class="sxs-lookup"><span data-stu-id="a2fda-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="a2fda-104">Giriş dilleri listesine dil eklenerek yazım denetleyicisi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a2fda-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="a2fda-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="a2fda-105">Suggestion</span></span>|<span data-ttu-id="a2fda-106">Yazım denetimi yapılacak dil veya metnin Windows 10'da çalışmak için yazım denetimi için giriş dili olarak eklenmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a2fda-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="a2fda-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a2fda-107">Scope</span></span>|<span data-ttu-id="a2fda-108">Edge</span><span class="sxs-lookup"><span data-stu-id="a2fda-108">Edge</span></span>|
|<span data-ttu-id="a2fda-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a2fda-109">Version</span></span>|<span data-ttu-id="a2fda-110">4.6</span><span class="sxs-lookup"><span data-stu-id="a2fda-110">4.6</span></span>|
|<span data-ttu-id="a2fda-111">Tür</span><span class="sxs-lookup"><span data-stu-id="a2fda-111">Type</span></span>|<span data-ttu-id="a2fda-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a2fda-112">Runtime</span></span>|
