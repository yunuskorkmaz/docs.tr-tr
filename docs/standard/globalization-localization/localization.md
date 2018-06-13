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
ms.openlocfilehash: 7fc995843c1e2f5977acbfe2158457d30ac355ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573919"
---
# <a name="localization"></a><span data-ttu-id="ba52a-102">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="ba52a-102">Localization</span></span>
<span data-ttu-id="ba52a-103">Yerelleştirme uygulama destekleyecek her kültür için yerelleştirilmiş sürümleri içine uygulamanın kaynaklarını çevirme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="ba52a-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="ba52a-104">Yalnızca tamamladıktan sonra yerelleştirme adıma devam etmemelisiniz [Yerelleştirilebilirlik gözden geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md) globalized uygulama yerelleştirme için hazır olduğunu doğrulamak için adım.</span><span class="sxs-lookup"><span data-stu-id="ba52a-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="ba52a-105">Yerelleştirme için hazır bir uygulama, iki kavramsal blokları, tüm kullanıcı arabirimi öğeleri içeren bir blok ve yürütülebilir kodu içeren bir blok ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ba52a-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="ba52a-106">Kullanıcı arabirimi bloğu yalnızca dizeleri, hata iletileri, iletişim kutuları, menüler, vb. bağımsız kültür için katıştırılmış nesne kaynakları gibi yerelleştirilebilir kullanıcı arabirimi öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba52a-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="ba52a-107">Kod bloğu tarafından desteklenen tüm kültürler kullanılacak yalnızca uygulama kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ba52a-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="ba52a-108">Ortak dil çalışma zamanı uygulamanın yürütülebilir kod kaynaklarıyla ayıran bir uydu derleme kaynağı modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="ba52a-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="ba52a-109">Bu model uygulama hakkında daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakları](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba52a-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="ba52a-110">Uygulamanızın yerelleştirilmiş her sürümü için hedef kültürle için uygun dili erişimcisine yerelleştirilmiş kullanıcı arabirimi blok içeren yeni bir uydu derleme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba52a-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="ba52a-111">Tüm kültürler için kod bloğu aynı kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba52a-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="ba52a-112">Kod bloğu ile kullanıcı arabirimi bloğunun yerelleştirilmiş bir sürümün birleşimi, uygulamanızın yerelleştirilmiş bir sürümün üretir.</span><span class="sxs-lookup"><span data-stu-id="ba52a-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="ba52a-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe), hızlı bir şekilde Windows Forms için hedef kültürlere yerelleştirme sayesinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba52a-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="ba52a-114">Bu aracı kullanmayla ilgili daha fazla bilgi için bkz: [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="ba52a-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba52a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba52a-115">See Also</span></span>  
 [<span data-ttu-id="ba52a-116">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="ba52a-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="ba52a-117">Yerelleştirilebilirlik Gözden Geçirmesi</span><span class="sxs-lookup"><span data-stu-id="ba52a-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 [<span data-ttu-id="ba52a-118">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="ba52a-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="ba52a-119">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ba52a-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
