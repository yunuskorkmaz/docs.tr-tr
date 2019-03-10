---
title: .NET Framework ile Özel Windows Forms Denetimleri Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 3d628d75b75c311c266648886b3b971c4833d172
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716445"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="c6572-102">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="c6572-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="c6572-103">Windows Forms denetimleri, kullanıcı arabiriminin işlevselliğini kapsülleyen ve istemci tarafı Windows tabanlı uygulamalarda kullanılır, yeniden kullanılabilir bileşenleridir.</span><span class="sxs-lookup"><span data-stu-id="c6572-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="c6572-104">Yalnızca Windows Forms pek çok kullanıma hazır denetimi sağlar, ayrıca kendi denetimleri geliştirmek için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6572-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="c6572-105">Mevcut denetimleri birleştirmek, mevcut denetimleri genişletmek veya kendi özel denetimler yazar.</span><span class="sxs-lookup"><span data-stu-id="c6572-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="c6572-106">Bu bölümde, arka plan bilgileri ve Windows Forms denetimleri geliştirmenize yardımcı olacak örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6572-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6572-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c6572-107">In This Section</span></span>  
 [<span data-ttu-id="c6572-108">Windows Forms'da Denetimlerin Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6572-108">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="c6572-109">Windows Forms uygulamalarında denetimlerin kullanımına temel öğeleri vurgular.</span><span class="sxs-lookup"><span data-stu-id="c6572-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="c6572-110">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="c6572-110">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="c6572-111">Özel denetimler ile yazar farklı türlerde açıklar <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c6572-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="c6572-112">Windows Forms Denetimi Geliştirmenin Esasları</span><span class="sxs-lookup"><span data-stu-id="c6572-112">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="c6572-113">Bir Windows Forms denetimi geliştirme ilk adımlar anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6572-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="c6572-114">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="c6572-114">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="c6572-115">Windows Forms denetimlerine özellikleri ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6572-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c6572-116">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="c6572-116">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="c6572-117">Windows Forms denetimlerinde olay tanımlama ve işlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6572-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c6572-118">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6572-118">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="c6572-119">Özellikleri veya diğer üyeleri özel denetimler ve bileşenlerinizi uygulayabilirsiniz öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6572-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="c6572-120">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="c6572-120">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="c6572-121">Denetimleri özelleştirme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6572-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="c6572-122">Windows Forms Denetimlerindeki Düzenler</span><span class="sxs-lookup"><span data-stu-id="c6572-122">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="c6572-123">Formlar ve denetimler için Gelişmiş düzenleri oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6572-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="c6572-124">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="c6572-124">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="c6572-125">Çok iş parçacıklı denetimleri uygulama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6572-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c6572-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c6572-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="c6572-127">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="c6572-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="c6572-128">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="c6572-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c6572-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c6572-129">Related Sections</span></span>  
 <span data-ttu-id="c6572-130">[Bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c6572-130">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="c6572-131">Böylece bunlar görsel tasarımcılar, tasarım zamanında doğru bir şekilde görüntülenir, bileşenleri ve denetimleri uygulamak için meta veri öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c6572-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="c6572-132">[Tasarım zamanı desteği sunma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c6572-132">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="c6572-133">Sınıflar gibi düzenleyiciler ve tasarımcılar, tasarım zamanı desteği sağlayan uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6572-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="c6572-134">[Nasıl yapılır: Lisans bileşenleri ve denetimleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c6572-134">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="c6572-135">Lisans, bir denetim ya da bileşen uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6572-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="c6572-136">Ayrıca bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c6572-136">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
