---
title: Windows Forms Denetimlerindeki Özellikler
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747407"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="99041-102">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="99041-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="99041-103">Bir Windows Forms denetimi birçok özellikleri formu temel sınıf devralan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99041-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99041-104">Bu gibi özellikleri içeren <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>ve diğer birçok.</span><span class="sxs-lookup"><span data-stu-id="99041-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="99041-105">Devralınan özellikler hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99041-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="99041-106">Devralınan özellikler geçersiz kılma denetiminizi yapabilir yeni özelliklerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="99041-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99041-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="99041-107">In This Section</span></span>  
 [<span data-ttu-id="99041-108">Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="99041-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="99041-109">Bir özelliği bir özel denetim veya bileşen için uygulama işlemini gösterir ve tasarım ortamına özelliği tümleştirme işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="99041-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="99041-110">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="99041-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="99041-111">Özel denetim veya bileşen için varsayılan özellik değerlerini tanımlayabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99041-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="99041-112">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="99041-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="99041-113">Özellik değişikliği bildirimleri bir özellik değeri değiştiğinde etkinleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="99041-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="99041-114">Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma</span><span class="sxs-lookup"><span data-stu-id="99041-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="99041-115">Bağlı denetimlerin özelliklerini özel bileşik denetim olarak kullanıma sunma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99041-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="99041-116">Özel Denetimlerde Yöntem Uygulama</span><span class="sxs-lookup"><span data-stu-id="99041-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="99041-117">Özel denetimleri ve bileşenleri yöntemleri uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="99041-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="99041-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="99041-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="99041-119">Bileşik denetimler uygulamak için temel sınıf belgeler.</span><span class="sxs-lookup"><span data-stu-id="99041-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="99041-120">Belirten özniteliği belgeleri <xref:System.ComponentModel.TypeConverter> bir özel özellik türü için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="99041-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="99041-121">Belirten özniteliği belgeleri <xref:System.Drawing.Design.UITypeEditor> özel bir özellik için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="99041-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99041-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="99041-122">Related Sections</span></span>  
 [<span data-ttu-id="99041-123">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99041-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="99041-124">Özellikleri veya diğer üyeleri özel denetimler ve bileşenlerinizi uygulayabilirsiniz öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99041-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="99041-125">Bileşenler için tasarım zamanı öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="99041-125">Design-Time Attributes for Components</span></span>](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="99041-126">Böylece bunlar görsel tasarımcılar, tasarım zamanında doğru bir şekilde görüntülenir, bileşenleri ve denetimleri uygulamak için meta veri öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="99041-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="99041-127">Tasarım zamanı desteği sunma</span><span class="sxs-lookup"><span data-stu-id="99041-127">Extending Design-Time Support</span></span>](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="99041-128">Sınıflar gibi düzenleyiciler ve tasarımcılar, tasarım zamanı desteği sağlayan uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="99041-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
