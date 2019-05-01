---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664547"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="bd908-101">WPF yazım metin özellikli denetimlerinde işletim sisteminin giriş dili listede olmayan dilleri için Windows 10'da çalışmaz</span><span class="sxs-lookup"><span data-stu-id="bd908-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bd908-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bd908-102">Details</span></span>|<span data-ttu-id="bd908-103">Windows 10'da çalıştırırken, Platform yazım denetimi özelliklerini yalnızca diller listesinde mevcut diller için kullanılabilir olmadığından yazım denetleyicisi metin özellikli WPF denetimleri için çalışmayabilir. Windows 10'daki bir dil kullanılabilir klavyeler listesine eklendiğinde Windows otomatik olarak indirir ve karşılık gelen bir özellik, yazım denetimi özellikleri sağlayan isteğe bağlı (FOD) paketi yükler.</span><span class="sxs-lookup"><span data-stu-id="bd908-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="bd908-104">Dil diller listesine ekleyerek, yazım denetleyicisi desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="bd908-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="bd908-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="bd908-105">Suggestion</span></span>|<span data-ttu-id="bd908-106">Windows 10'da çalışmak için yazım denetimi için bir giriş dili olarak dili veya yazım iade edilecek metin eklenmelidir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bd908-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="bd908-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bd908-107">Scope</span></span>|<span data-ttu-id="bd908-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="bd908-108">Edge</span></span>|
|<span data-ttu-id="bd908-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bd908-109">Version</span></span>|<span data-ttu-id="bd908-110">4.6</span><span class="sxs-lookup"><span data-stu-id="bd908-110">4.6</span></span>|
|<span data-ttu-id="bd908-111">Tür</span><span class="sxs-lookup"><span data-stu-id="bd908-111">Type</span></span>|<span data-ttu-id="bd908-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="bd908-112">Runtime</span></span>|
