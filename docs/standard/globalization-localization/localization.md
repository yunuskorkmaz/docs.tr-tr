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
ms.openlocfilehash: ee7de15130644e63b17a6d067c5cce9088d199a0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521196"
---
# <a name="localization"></a><span data-ttu-id="d2d87-102">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2d87-102">Localization</span></span>
<span data-ttu-id="d2d87-103">Yerelleştirme uygulama destekleyen her bir kültür için yerelleştirilmiş sürüm uygulamanın kaynaklarını çevirmeyi işlemidir.</span><span class="sxs-lookup"><span data-stu-id="d2d87-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="d2d87-104">Yalnızca tamamladıktan sonra yerelleştirme adıma devam etmelisiniz [Yerelleştirilebilirlik gözden geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md) yazılırlar yerelleştirme için hazır olduğunu doğrulamak için adım.</span><span class="sxs-lookup"><span data-stu-id="d2d87-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="d2d87-105">Yerelleştirme için hazır bir uygulama iki kavramsal blokları, tüm kullanıcı arabirimi öğeleri içeren bir blok ve yürütülebilir kod içeren bir blok ayrılır.</span><span class="sxs-lookup"><span data-stu-id="d2d87-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="d2d87-106">Kullanıcı arabirimi bloğu, dizeler, hata iletileri, iletişim kutuları, menüler, vb. bağımsız kültür için katıştırılmış nesne kaynakları gibi yalnızca yerelleştirilebilir kullanıcı arabirimi öğeleri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d2d87-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="d2d87-107">Kod bloğu tüm desteklenen kültürler tarafından kullanılmak üzere yalnızca uygulama kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d2d87-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="d2d87-108">Ortak dil çalışma zamanı, bir uygulamanın yürütülebilir kodunun kaynaklarından ayıran bir uydu derleme kaynağı modeli destekler.</span><span class="sxs-lookup"><span data-stu-id="d2d87-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="d2d87-109">Bu model uygulama hakkında daha fazla bilgi için bkz. [masaüstü uygulamalarında kaynakların](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2d87-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="d2d87-110">Uygulamanızı yerelleştirilmiş her sürümü için yerelleştirilmiş kullanıcı arabirimi blok hedef kültüre uygun dili erişimcisine içeren yeni bir uydu derlemesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2d87-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="d2d87-111">Kod bloğu tüm kültürler için aynı kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2d87-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="d2d87-112">Kullanıcı arabirimi blok kod bloğu ile yerelleştirilmiş bir sürümünü birleşimi, uygulamanızın yerelleştirilmiş bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2d87-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="d2d87-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Sağlayan Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe), hızlı bir şekilde hedef kültür için Windows formlarını yerelleştirmeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d2d87-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="d2d87-114">Bu aracı kullanma hakkında daha fazla bilgi için bkz: [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="d2d87-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d87-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2d87-115">See also</span></span>

- [<span data-ttu-id="d2d87-116">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2d87-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
- [<span data-ttu-id="d2d87-117">Yerelleştirilebilirlik Gözden Geçirmesi</span><span class="sxs-lookup"><span data-stu-id="d2d87-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
- [<span data-ttu-id="d2d87-118">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2d87-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
- [<span data-ttu-id="d2d87-119">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d2d87-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
