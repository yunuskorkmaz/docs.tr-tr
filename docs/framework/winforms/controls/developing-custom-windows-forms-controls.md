---
title: .NET Framework ile Özel Windows Forms Denetimleri Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 6ab459f37e825d71163e375e10f30fbe3e23911a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525542"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="c7991-102">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="c7991-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="c7991-103">Windows Forms denetimleri, kullanıcı arabiriminin işlevselliğini kapsülleyen ve istemci tarafı Windows tabanlı uygulamalarda kullanılır, yeniden kullanılabilir bileşenleridir.</span><span class="sxs-lookup"><span data-stu-id="c7991-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="c7991-104">Yalnızca Windows Forms pek çok kullanıma hazır denetimi sağlar, ayrıca kendi denetimleri geliştirmek için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7991-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="c7991-105">Mevcut denetimleri birleştirmek, mevcut denetimleri genişletmek veya kendi özel denetimler yazar.</span><span class="sxs-lookup"><span data-stu-id="c7991-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="c7991-106">Bu bölümde, arka plan bilgileri ve Windows Forms denetimleri geliştirmenize yardımcı olacak örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7991-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7991-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c7991-107">In This Section</span></span>  
 [<span data-ttu-id="c7991-108">Windows Forms'da Denetimlerin Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c7991-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="c7991-109">Windows Forms uygulamalarında denetimlerin kullanımına temel öğeleri vurgular.</span><span class="sxs-lookup"><span data-stu-id="c7991-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="c7991-110">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="c7991-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="c7991-111">Özel denetimler ile yazar farklı türlerde açıklar <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c7991-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="c7991-112">Windows Forms Denetimi Geliştirmenin Esasları</span><span class="sxs-lookup"><span data-stu-id="c7991-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="c7991-113">Bir Windows Forms denetimi geliştirme ilk adımlar anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7991-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="c7991-114">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="c7991-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="c7991-115">Windows Forms denetimlerine özellikleri ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7991-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c7991-116">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="c7991-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="c7991-117">Windows Forms denetimlerinde olay tanımlama ve işlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7991-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c7991-118">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7991-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="c7991-119">Özellikleri veya diğer üyeleri özel denetimler ve bileşenlerinizi uygulayabilirsiniz öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7991-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="c7991-120">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="c7991-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="c7991-121">Denetimleri özelleştirme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7991-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="c7991-122">Windows Forms Denetimlerindeki Düzenler</span><span class="sxs-lookup"><span data-stu-id="c7991-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="c7991-123">Formlar ve denetimler için Gelişmiş düzenleri oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7991-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="c7991-124">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="c7991-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="c7991-125">Çok iş parçacıklı denetimleri uygulama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7991-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c7991-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c7991-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="c7991-127">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="c7991-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="c7991-128">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="c7991-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7991-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c7991-129">Related Sections</span></span>  
 [<span data-ttu-id="c7991-130">Bileşenler için tasarım zamanı öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7991-130">Design-Time Attributes for Components</span></span>](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="c7991-131">Böylece bunlar görsel tasarımcılar, tasarım zamanında doğru bir şekilde görüntülenir, bileşenleri ve denetimleri uygulamak için meta veri öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c7991-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="c7991-132">Tasarım zamanı desteği sunma</span><span class="sxs-lookup"><span data-stu-id="c7991-132">Extending Design-Time Support</span></span>](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="c7991-133">Sınıflar gibi düzenleyiciler ve tasarımcılar, tasarım zamanı desteği sağlayan uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7991-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="c7991-134">Nasıl yapılır: Lisans bileşenleri ve denetimleri</span><span class="sxs-lookup"><span data-stu-id="c7991-134">How to: License Components and Controls</span></span>](https://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="c7991-135">Lisans, bir denetim ya da bileşen uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7991-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="c7991-136">Ayrıca bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](https://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c7991-136">Also see [Developing Windows Forms Controls at Design Time](https://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>
