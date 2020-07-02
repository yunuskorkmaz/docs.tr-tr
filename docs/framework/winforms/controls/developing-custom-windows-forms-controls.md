---
title: Özel Denetim geliştirme
description: Windows form denetimleri hakkında bilgi edinin. Özellikle, var olan denetimleri birleştirmeyi, var olan denetimleri genişletmeyi ve kendi özel denetimlerinizi yazarla öğrenirsiniz.
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 12013496c9650489fdd7512206317000fc0ec78c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618382"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="e9479-104">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="e9479-104">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="e9479-105">Windows Forms denetimleri, Kullanıcı arabirimi işlevselliğini kapsülleyen ve istemci tarafı Windows tabanlı uygulamalarda kullanılan yeniden kullanılabilir bileşenlerdir.</span><span class="sxs-lookup"><span data-stu-id="e9479-105">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="e9479-106">Yalnızca çok sayıda kullanıma kullanım denetimi sunmadığından Windows Forms, kendi denetimlerinizi geliştirmek için de altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9479-106">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="e9479-107">Varolan denetimleri birleştirebilir, varolan denetimleri genişletebilir veya kendi özel denetimlerinizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9479-107">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="e9479-108">Bu bölüm, Windows Forms denetimleri geliştirmenize yardımcı olacak arka plan bilgileri ve örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9479-108">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9479-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e9479-109">In This Section</span></span>  
 [<span data-ttu-id="e9479-110">Windows Forms'da Denetimlerin Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9479-110">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="e9479-111">Windows Forms uygulamalarında denetimleri kullanmanın temel öğelerini vurgular.</span><span class="sxs-lookup"><span data-stu-id="e9479-111">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="e9479-112">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="e9479-112">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="e9479-113">Ad alanı ile yazoluşturabileceğiniz farklı özel denetim türlerini açıklar <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9479-113">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="e9479-114">Windows Forms Denetimi Geliştirmenin Esasları</span><span class="sxs-lookup"><span data-stu-id="e9479-114">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="e9479-115">Windows Forms Denetim geliştirme içindeki ilk adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9479-115">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="e9479-116">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="e9479-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="e9479-117">Windows Forms denetimlerine özelliklerin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9479-117">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="e9479-118">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="e9479-118">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="e9479-119">Windows Forms Denetimlerinde olayların nasıl işleneceğini ve tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9479-119">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="e9479-120">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9479-120">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="e9479-121">Özel denetimlerinizin ve bileşenlerinizin özelliklerine veya diğer üyelerine uygulayabileceğiniz öznitelikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9479-121">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="e9479-122">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="e9479-122">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="e9479-123">Denetimlerinizin görünümünü nasıl özelleştireceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9479-123">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="e9479-124">Windows Forms Denetimlerindeki Düzenler</span><span class="sxs-lookup"><span data-stu-id="e9479-124">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="e9479-125">Denetimleriniz ve formlarınız için gelişmiş düzenler oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9479-125">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="e9479-126">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="e9479-126">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="e9479-127">Çok iş parçacıklı denetimlerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9479-127">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e9479-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e9479-128">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="e9479-129">Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="e9479-129">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="e9479-130">Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="e9479-130">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9479-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e9479-131">Related Sections</span></span>  
 <span data-ttu-id="e9479-132">[Bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e9479-132">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="e9479-133">Görsel tasarımcılarda tasarım zamanında doğru görüntülenebilmesi için bileşenlere ve denetimlere uygulanacak meta veri özniteliklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="e9479-133">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="e9479-134">[Tasarım Zamanı Desteği Sunma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e9479-134">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="e9479-135">Tasarım zamanı desteği sağlayan düzenleyiciler ve tasarımcılar gibi sınıfların nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9479-135">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="e9479-136">[Nasıl yapılır: Lisans Bileşenleri ve Denetimleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e9479-136">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="e9479-137">Denetim veya bileşeninizdeki lisanslamanın nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9479-137">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="e9479-138">Ayrıca bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="e9479-138">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
