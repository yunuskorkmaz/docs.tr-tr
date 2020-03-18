---
title: Yerelleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 89851c42570f301bee8a3eca744eb5d069347d4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120868"
---
# <a name="localization"></a><span data-ttu-id="dcc2c-102">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="dcc2c-102">Localization</span></span>

<span data-ttu-id="dcc2c-103">Yerelleştirme, uygulamanın kaynaklarını, uygulamanın destekleyeceği her kültür için yerelleştirilmiş sürümlere çevirme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="dcc2c-104">Globalized uygulamanın yerelleştirme için hazır olduğunu doğrulamak için yerelleştirme adımına yalnızca [Yerelleştirilebilirlik Gözden Geçirme](../../../docs/standard/globalization-localization/localizability-review.md) adımını tamamladıktan sonra devam etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="dcc2c-105">Yerelleştirme için hazır bir uygulama iki kavramsal bloka ayrılır: tüm kullanıcı arabirimi öğelerini içeren bir blok ve yürütülebilir kod içeren bir blok.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="dcc2c-106">Kullanıcı arabirimi bloğu, yalnızca dizeleri, hata iletileri, iletişim kutuları, menüler, katıştırılmış nesne kaynakları ve benzeri nötr kültür için gibi yerelleştirilebilir kullanıcı arabirimi öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="dcc2c-107">Kod bloğu yalnızca desteklenen tüm kültürler tarafından kullanılacak uygulama kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="dcc2c-108">Ortak dil çalışma süresi, bir uygulamanın yürütülebilir kodunu kaynaklarından ayıran bir uydu derleme kaynak modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="dcc2c-109">Bu modeli uygulama hakkında daha fazla bilgi için [.NET'teki Kaynaklar'a](../../../docs/framework/resources/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-109">For more information about implementing this model, see [Resources in .NET](../../../docs/framework/resources/index.md).</span></span>

<span data-ttu-id="dcc2c-110">Uygulamanızın her yerelleştirilmiş sürümü için, hedef kültür için uygun dile çevrilmiş yerelleştirilmiş kullanıcı arabirimi bloğunu içeren yeni bir uydu derlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="dcc2c-111">Tüm kültürler için kod bloğu aynı kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="dcc2c-112">Kullanıcı arabirimi bloğunun yerelleştirilmiş bir sürümünün kod bloğuyla birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="dcc2c-113">Windows Yazılım Geliştirme Kiti (SDK), hedef kültürler için Windows Formlarını hızla yerelleştirmenize olanak tanıyan Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe) sağlar.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-113">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="dcc2c-114">Bu aracı kullanma hakkında daha fazla bilgi için [Winres.exe (Windows Forms Resource Editor) (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dcc2c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcc2c-115">See also</span></span>

- [<span data-ttu-id="dcc2c-116">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="dcc2c-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="dcc2c-117">Yerelleştirilebilirlik İnceleme</span><span class="sxs-lookup"><span data-stu-id="dcc2c-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)
- [<span data-ttu-id="dcc2c-118">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="dcc2c-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="dcc2c-119">Masaüstü Uygulamalarında Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dcc2c-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
