---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621448"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="2989d-101">Metin özellikli denetimlerde WPF yazım denetimi, işletim sisteminin giriş dili listesinde olmayan diller için Windows 10 ' da çalışmaz</span><span class="sxs-lookup"><span data-stu-id="2989d-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="2989d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2989d-102">Details</span></span>

<span data-ttu-id="2989d-103">Windows 10 ' da çalışırken, platform yazım denetimi özellikleri yalnızca giriş dilleri listesinde bulunan diller için kullanılabilir olduğundan, yazım denetleyicisi WPF metin özellikli denetimler için çalışmayabilir. Windows 10 ' da, kullanılabilir klavyeler listesine bir dil eklendiğinde, Windows otomatik olarak yazım denetimi özellikleri sağlayan ilgili bir Isteğe bağlı Özellik (FOD) paketini indirir ve yükler.</span><span class="sxs-lookup"><span data-stu-id="2989d-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="2989d-104">Dili giriş dilleri listesine ekleyerek, yazım denetleyicisi desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="2989d-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2989d-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="2989d-105">Suggestion</span></span>

<span data-ttu-id="2989d-106">Yazım denetimi yapılacak dilin veya metnin, Windows 10 ' da çalışmak üzere yazım denetimi yapmak için bir giriş dili olarak eklenmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2989d-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="2989d-107">Name</span><span class="sxs-lookup"><span data-stu-id="2989d-107">Name</span></span>    | <span data-ttu-id="2989d-108">Değer</span><span class="sxs-lookup"><span data-stu-id="2989d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2989d-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2989d-109">Scope</span></span>   |<span data-ttu-id="2989d-110">Edge</span><span class="sxs-lookup"><span data-stu-id="2989d-110">Edge</span></span>|
|<span data-ttu-id="2989d-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2989d-111">Version</span></span>|<span data-ttu-id="2989d-112">4.6</span><span class="sxs-lookup"><span data-stu-id="2989d-112">4.6</span></span>|
|<span data-ttu-id="2989d-113">Tür</span><span class="sxs-lookup"><span data-stu-id="2989d-113">Type</span></span>|<span data-ttu-id="2989d-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="2989d-114">Runtime</span></span>|
