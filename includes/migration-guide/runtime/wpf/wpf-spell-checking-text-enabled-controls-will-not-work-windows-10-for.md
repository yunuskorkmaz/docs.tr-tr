---
ms.openlocfilehash: 97ca78e154eb25e863256e06caa119fe753bc344
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761421"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="98266-101">WPF yazım metin özellikli denetimlerinde işletim sisteminin giriş dili listede olmayan dilleri için Windows 10'da çalışmaz</span><span class="sxs-lookup"><span data-stu-id="98266-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="98266-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="98266-102">Details</span></span>|<span data-ttu-id="98266-103">Windows 10'da çalıştırırken, Platform yazım denetimi özelliklerini yalnızca diller listesinde mevcut diller için kullanılabilir olmadığından yazım denetleyicisi metin özellikli WPF denetimleri için çalışmayabilir. Windows 10'daki bir dil kullanılabilir klavyeler listesine eklendiğinde Windows otomatik olarak indirir ve karşılık gelen bir özellik, yazım denetimi özellikleri sağlayan isteğe bağlı (FOD) paketi yükler.</span><span class="sxs-lookup"><span data-stu-id="98266-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="98266-104">Dil diller listesine ekleyerek, yazım denetleyicisi desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="98266-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="98266-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="98266-105">Suggestion</span></span>|<span data-ttu-id="98266-106">Windows 10'da çalışmak için yazım denetimi için bir giriş dili olarak dili veya yazım iade edilecek metin eklenmelidir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="98266-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="98266-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="98266-107">Scope</span></span>|<span data-ttu-id="98266-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="98266-108">Edge</span></span>|
|<span data-ttu-id="98266-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="98266-109">Version</span></span>|<span data-ttu-id="98266-110">4.6</span><span class="sxs-lookup"><span data-stu-id="98266-110">4.6</span></span>|
|<span data-ttu-id="98266-111">Tür</span><span class="sxs-lookup"><span data-stu-id="98266-111">Type</span></span>|<span data-ttu-id="98266-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="98266-112">Runtime</span></span>|

