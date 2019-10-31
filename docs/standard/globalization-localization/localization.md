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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120868"
---
# <a name="localization"></a><span data-ttu-id="f07d8-102">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="f07d8-102">Localization</span></span>

<span data-ttu-id="f07d8-103">Yerelleştirme, uygulamanın destekleyeceği her kültür için bir uygulamanın kaynaklarını yerelleştirilmiş sürümlere çevirme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="f07d8-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="f07d8-104">Genelleştirilmiş uygulamasının yerelleştirme için hazırlanmaya devam ettiğini doğrulamak için yerelleştirme adımına yalnızca [Yerelleştirilebilirlik gözden geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md) adımını tamamladıktan sonra ilerlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f07d8-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="f07d8-105">Yerelleştirme için hazırlanma bir uygulama iki kavramsal blok halinde ayrılmıştır: tüm Kullanıcı arabirimi öğelerini ve yürütülebilir kodu içeren bir bloğu içeren bir blok.</span><span class="sxs-lookup"><span data-stu-id="f07d8-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="f07d8-106">Kullanıcı arabirimi bloğu, bağımsız kültür için yalnızca dizeler, hata iletileri, iletişim kutuları, menüler, katıştırılmış nesne kaynakları gibi yerelleştirilebilir kullanıcı arabirimi öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f07d8-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="f07d8-107">Kod bloğu yalnızca desteklenen tüm kültürler tarafından kullanılacak uygulama kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f07d8-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="f07d8-108">Ortak dil çalışma zamanı, bir uygulamanın yürütülebilir kodunu kaynaklarından ayıran bir uydu derleme kaynak modeli destekler.</span><span class="sxs-lookup"><span data-stu-id="f07d8-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="f07d8-109">Bu modeli uygulama hakkında daha fazla bilgi için bkz. [.net 'Teki kaynaklar](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="f07d8-109">For more information about implementing this model, see [Resources in .NET](../../../docs/framework/resources/index.md).</span></span>

<span data-ttu-id="f07d8-110">Uygulamanızın yerelleştirilmiş her sürümü için, hedef kültür için uygun dile çevrilmiş yerelleştirilmiş kullanıcı arabirimi bloğunu içeren yeni bir uydu derlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f07d8-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="f07d8-111">Tüm kültürlerin kod bloğu aynı kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f07d8-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="f07d8-112">Kod bloğu ile Kullanıcı arabirimi bloğunun yerelleştirilmiş bir sürümünün birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f07d8-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="f07d8-113">Windows yazılım geliştirme seti (SDK), hedef kültürler için Windows Forms hızlı bir şekilde yerelleştirebilmenizi sağlayan Windows Forms Kaynak Düzenleyicisi 'Ni (Winres. exe) sağlar.</span><span class="sxs-lookup"><span data-stu-id="f07d8-113">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="f07d8-114">Bu aracı kullanma hakkında daha fazla bilgi için bkz. [Winres. exe (Windows Forms Kaynak Düzenleyicisi)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="f07d8-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f07d8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f07d8-115">See also</span></span>

- [<span data-ttu-id="f07d8-116">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="f07d8-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="f07d8-117">Yerelleştirilebilirlik Gözden Geçirmesi</span><span class="sxs-lookup"><span data-stu-id="f07d8-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)
- [<span data-ttu-id="f07d8-118">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="f07d8-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="f07d8-119">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f07d8-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
