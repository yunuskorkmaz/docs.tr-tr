---
title: Denetimlerin özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741172"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="7d61e-102">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="7d61e-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="7d61e-103">Windows Forms denetim, temel sınıf <xref:System.Windows.Forms.Control?displayProperty=nameWithType>birçok özellik formunu devralır.</span><span class="sxs-lookup"><span data-stu-id="7d61e-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7d61e-104">Bunlar <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>ve diğer birçok özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="7d61e-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="7d61e-105">Devralınan özellikler hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d61e-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7d61e-106">Denetiminizin devralınan özelliklerini geçersiz kılabilir ve yeni özellikler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d61e-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d61e-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7d61e-107">In This Section</span></span>  
 [<span data-ttu-id="7d61e-108">Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="7d61e-108">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="7d61e-109">Özel denetim veya bileşen için bir özelliğin nasıl uygulanacağını gösterir ve özelliğin tasarım ortamıyla nasıl tümleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d61e-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="7d61e-110">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="7d61e-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="7d61e-111">Özel bir denetim veya bileşen için varsayılan özellik değerlerinin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d61e-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="7d61e-112">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="7d61e-112">Property-Changed Events</span></span>](property-changed-events.md)  
 <span data-ttu-id="7d61e-113">Özellik değeri değiştiğinde özellik değişikliği bildirimlerinin nasıl etkinleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d61e-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="7d61e-114">Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma</span><span class="sxs-lookup"><span data-stu-id="7d61e-114">How to: Expose Properties of Constituent Controls</span></span>](how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="7d61e-115">Özel bir bileşik denetimde bileşen denetimlerinin özelliklerinin nasıl gösterileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d61e-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="7d61e-116">Özel Denetimlerde Yöntem Uygulama</span><span class="sxs-lookup"><span data-stu-id="7d61e-116">Method Implementation in Custom Controls</span></span>](method-implementation-in-custom-controls.md)  
 <span data-ttu-id="7d61e-117">Özel denetimlerde ve bileşenlerde yöntemlerin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d61e-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7d61e-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7d61e-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="7d61e-119">Bileşik denetimlerin uygulanması için temel sınıfı belgeler.</span><span class="sxs-lookup"><span data-stu-id="7d61e-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="7d61e-120">Özel özellik türü için kullanılacak <xref:System.ComponentModel.TypeConverter> belirten özniteliği belgeler.</span><span class="sxs-lookup"><span data-stu-id="7d61e-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="7d61e-121">Özel bir özellik için kullanılacak <xref:System.Drawing.Design.UITypeEditor> belirten özniteliği belgeler.</span><span class="sxs-lookup"><span data-stu-id="7d61e-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d61e-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7d61e-122">Related Sections</span></span>  
 [<span data-ttu-id="7d61e-123">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d61e-123">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="7d61e-124">Özel denetimlerinizin ve bileşenlerinizin özelliklerine veya diğer üyelerine uygulayabileceğiniz öznitelikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d61e-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 <span data-ttu-id="7d61e-125">[Bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7d61e-125">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="7d61e-126">Görsel tasarımcılarda tasarım zamanında doğru görüntülenebilmesi için bileşenlere ve denetimlere uygulanacak meta veri özniteliklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="7d61e-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="7d61e-127">[Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7d61e-127">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="7d61e-128">Tasarım zamanı desteği sağlayan düzenleyiciler ve tasarımcılar gibi sınıfların nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d61e-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
