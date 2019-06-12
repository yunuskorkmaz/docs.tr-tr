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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79ec24d16b43bd8e1312b3425e618adf163edd24
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834017"
---
# <a name="localization"></a><span data-ttu-id="e73a0-102">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="e73a0-102">Localization</span></span>

<span data-ttu-id="e73a0-103">Yerelleştirme uygulama destekleyen her bir kültür için yerelleştirilmiş sürüm uygulamanın kaynaklarını çevirmeyi işlemidir.</span><span class="sxs-lookup"><span data-stu-id="e73a0-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="e73a0-104">Yalnızca tamamladıktan sonra yerelleştirme adıma devam etmelisiniz [Yerelleştirilebilirlik gözden geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md) yazılırlar yerelleştirme için hazır olduğunu doğrulamak için adım.</span><span class="sxs-lookup"><span data-stu-id="e73a0-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="e73a0-105">Yerelleştirme için hazır bir uygulama iki kavramsal bloklarda ayrılır: tüm kullanıcı arabirimi öğeleri ve yürütülebilir kod içeren bir bloğu içeren bir blok.</span><span class="sxs-lookup"><span data-stu-id="e73a0-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="e73a0-106">Kullanıcı arabirimi bloğu, dizeler, hata iletileri, iletişim kutuları, menüler, vb. bağımsız kültür için katıştırılmış nesne kaynakları gibi yalnızca yerelleştirilebilir kullanıcı arabirimi öğeleri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e73a0-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="e73a0-107">Kod bloğu tüm desteklenen kültürler tarafından kullanılmak üzere yalnızca uygulama kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e73a0-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="e73a0-108">Ortak dil çalışma zamanı, bir uygulamanın yürütülebilir kodunun kaynaklarından ayıran bir uydu derleme kaynağı modeli destekler.</span><span class="sxs-lookup"><span data-stu-id="e73a0-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="e73a0-109">Bu model uygulama hakkında daha fazla bilgi için bkz. [.NET kaynaklarında](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="e73a0-109">For more information about implementing this model, see [Resources in .NET](../../../docs/framework/resources/index.md).</span></span>

<span data-ttu-id="e73a0-110">Uygulamanızı yerelleştirilmiş her sürümü için yerelleştirilmiş kullanıcı arabirimi blok hedef kültüre uygun dili erişimcisine içeren yeni bir uydu derlemesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e73a0-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="e73a0-111">Kod bloğu tüm kültürler için aynı kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e73a0-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="e73a0-112">Kullanıcı arabirimi blok kod bloğu ile yerelleştirilmiş bir sürümünü birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e73a0-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="e73a0-113">Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe), hızlı bir şekilde hedef kültür için Windows formlarını yerelleştirmeye olanak tanır Windows Yazılım Geliştirme Seti (SDK) sağlar.</span><span class="sxs-lookup"><span data-stu-id="e73a0-113">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="e73a0-114">Bu aracı kullanma hakkında daha fazla bilgi için bkz: [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="e73a0-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e73a0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e73a0-115">See also</span></span>

- [<span data-ttu-id="e73a0-116">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="e73a0-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="e73a0-117">Yerelleştirilebilirlik Gözden Geçirmesi</span><span class="sxs-lookup"><span data-stu-id="e73a0-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)
- [<span data-ttu-id="e73a0-118">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="e73a0-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="e73a0-119">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e73a0-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
