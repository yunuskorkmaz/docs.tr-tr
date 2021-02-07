---
description: 'Daha fazla bilgi edinin: yerelleştirme'
title: Yerelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- culture, localization
- application development [.NET], localization
- globalization [.NET], localization
- code blocks
- international applications [.NET], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 0f84e406e35eb75cacf6daac32bbe26b4750738b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675799"
---
# <a name="localization"></a><span data-ttu-id="0863b-103">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="0863b-103">Localization</span></span>

<span data-ttu-id="0863b-104">Yerelleştirme, uygulamanın destekleyeceği her kültür için bir uygulamanın kaynaklarını yerelleştirilmiş sürümlere çevirme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="0863b-104">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="0863b-105">Genelleştirilmiş uygulamasının yerelleştirme için hazırlanmaya devam ettiğini doğrulamak için yerelleştirme adımına yalnızca [Yerelleştirilebilirlik gözden geçirmesi](localizability-review.md) adımını tamamladıktan sonra ilerlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0863b-105">You should proceed to the localization step only after completing the [Localizability Review](localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="0863b-106">Yerelleştirme için hazırlanma bir uygulama iki kavramsal blok halinde ayrılmıştır: tüm Kullanıcı arabirimi öğelerini ve yürütülebilir kodu içeren bir bloğu içeren bir blok.</span><span class="sxs-lookup"><span data-stu-id="0863b-106">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="0863b-107">Kullanıcı arabirimi bloğu, bağımsız kültür için yalnızca dizeler, hata iletileri, iletişim kutuları, menüler, katıştırılmış nesne kaynakları gibi yerelleştirilebilir kullanıcı arabirimi öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0863b-107">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="0863b-108">Kod bloğu yalnızca desteklenen tüm kültürler tarafından kullanılacak uygulama kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0863b-108">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="0863b-109">Ortak dil çalışma zamanı, bir uygulamanın yürütülebilir kodunu kaynaklarından ayıran bir uydu derleme kaynak modeli destekler.</span><span class="sxs-lookup"><span data-stu-id="0863b-109">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="0863b-110">Bu modeli uygulama hakkında daha fazla bilgi için bkz. [.net 'Teki kaynaklar](../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="0863b-110">For more information about implementing this model, see [Resources in .NET](../../framework/resources/index.md).</span></span>

<span data-ttu-id="0863b-111">Uygulamanızın yerelleştirilmiş her sürümü için, hedef kültür için uygun dile çevrilmiş yerelleştirilmiş kullanıcı arabirimi bloğunu içeren yeni bir uydu derlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0863b-111">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="0863b-112">Tüm kültürlerin kod bloğu aynı kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0863b-112">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="0863b-113">Kod bloğu ile Kullanıcı arabirimi bloğunun yerelleştirilmiş bir sürümünün birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0863b-113">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="0863b-114">Windows yazılım geliştirme seti (SDK), hedef kültürler için Windows Forms hızlı bir şekilde yerelleştirebilmenizi sağlayan Windows Forms Kaynak Düzenleyicisi (Winres.exe) sağlar.</span><span class="sxs-lookup"><span data-stu-id="0863b-114">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="0863b-115">Bu aracı kullanma hakkında daha fazla bilgi için bkz. [Winres.exe (Windows Forms Kaynak Düzenleyicisi)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="0863b-115">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0863b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0863b-116">See also</span></span>

- [<span data-ttu-id="0863b-117">Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="0863b-117">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="0863b-118">Yerelleştirilebilirlik Incelemesi</span><span class="sxs-lookup"><span data-stu-id="0863b-118">Localizability Review</span></span>](localizability-review.md)
- [<span data-ttu-id="0863b-119">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="0863b-119">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="0863b-120">Masaüstü uygulamalarındaki kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0863b-120">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
