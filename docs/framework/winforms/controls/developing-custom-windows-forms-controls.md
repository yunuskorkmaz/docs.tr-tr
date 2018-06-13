---
title: .NET Framework ile Özel Windows Forms Denetimleri Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 935358664f93b6428b9153a9bcbed862aeee07ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528674"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="b3538-102">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="b3538-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="b3538-103">Windows Forms denetimleri, kullanıcı arabirimi işlevselliği kapsüllemek ve istemci tarafı Windows tabanlı uygulamalarda kullanılır yeniden kullanılabilir bileşenleridir.</span><span class="sxs-lookup"><span data-stu-id="b3538-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="b3538-104">Yalnızca Windows Forms pek çok kullanıma hazır denetimleri sağlar, ayrıca kendi denetimleri geliştirme için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3538-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="b3538-105">Var olan denetimleri birleştirmek, var olan denetimleri genişletmek veya kendi özel denetimler yazar.</span><span class="sxs-lookup"><span data-stu-id="b3538-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="b3538-106">Bu bölüm, arka plan bilgileri ve Windows Forms denetimleri geliştirmenize yardımcı olmak için örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3538-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3538-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b3538-107">In This Section</span></span>  
 [<span data-ttu-id="b3538-108">Windows Forms'da Denetimlerin Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3538-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="b3538-109">Windows Forms uygulamalarında denetimlerini kullanarak temel öğeleri vurgular.</span><span class="sxs-lookup"><span data-stu-id="b3538-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="b3538-110">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="b3538-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="b3538-111">Özel denetimler ile yazabilirsiniz farklı türleri açıklanmaktadır <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b3538-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="b3538-112">Windows Forms Denetimi Geliştirmenin Esasları</span><span class="sxs-lookup"><span data-stu-id="b3538-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="b3538-113">Bir Windows Forms denetimi geliştirme ilk adımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b3538-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="b3538-114">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="b3538-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="b3538-115">Windows Forms denetimlerine özellikleri eklemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3538-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b3538-116">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="b3538-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="b3538-117">İşlemek ve Windows Forms denetimlerinde olay tanımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3538-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b3538-118">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3538-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="b3538-119">Özellikleri veya diğer özel denetimleri ve bileşenleri üyeleri uygulayabilirsiniz öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3538-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="b3538-120">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="b3538-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="b3538-121">Denetimlerinizin görünümünü özelleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3538-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="b3538-122">Windows Forms Denetimlerindeki Düzenler</span><span class="sxs-lookup"><span data-stu-id="b3538-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="b3538-123">Gelişmiş düzenlerinin formlar ve denetimler için nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3538-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="b3538-124">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="b3538-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="b3538-125">Birden çok iş parçacıklı denetimler uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3538-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b3538-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b3538-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="b3538-127">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b3538-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="b3538-128">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b3538-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b3538-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b3538-129">Related Sections</span></span>  
 [<span data-ttu-id="b3538-130">Bileşenleri için tasarım zamanı öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3538-130">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="b3538-131">Böylece doğru görsel tasarımcılar tasarım zamanında görüntülendikleri bileşenleri ve denetimler uygulamak için meta veri öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="b3538-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="b3538-132">Tasarım zamanı desteği genişletme</span><span class="sxs-lookup"><span data-stu-id="b3538-132">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="b3538-133">Sınıfları düzenleyicileri ve tasarım zamanı desteği tasarımcıları gibi uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3538-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="b3538-134">Nasıl yapılır: Lisans bileşenleri ve denetimleri</span><span class="sxs-lookup"><span data-stu-id="b3538-134">How to: License Components and Controls</span></span>](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="b3538-135">Denetimi veya bileşeni içinde lisans uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3538-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="b3538-136">Ayrıca bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b3538-136">Also see [Developing Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>
