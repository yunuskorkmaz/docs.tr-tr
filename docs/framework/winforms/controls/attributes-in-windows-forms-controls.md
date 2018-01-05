---
title: "Windows Forms Denetimlerindeki Öznitelikler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13aad22dca249147e3037bcef6da755c264021db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="336ab-102">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="336ab-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="336ab-103">.NET Framework öznitelikleri özel denetimleri ve bileşenleri üyelerine uygulayabilirsiniz çeşitli sağlar.</span><span class="sxs-lookup"><span data-stu-id="336ab-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="336ab-104">Bazı bu öznitelikler bir sınıfın çalışma zamanı davranışını etkilemek ve diğer tasarım zamanı davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="336ab-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="336ab-105">Denetim ve bileşen özellikleri için öznitelikler</span><span class="sxs-lookup"><span data-stu-id="336ab-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="336ab-106">Aşağıdaki tabloda, özellikleri veya diğer özel denetimleri ve bileşenleri üyeleri uygulayabilirsiniz öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="336ab-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="336ab-107">Bu öznitelikler çoğunu kullanan bir örnek için bkz: [nasıl yapılır: Windows Forms denetimlerindeki öznitelikler uygulamak](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="336ab-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="336ab-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="336ab-108">Attribute</span></span>|<span data-ttu-id="336ab-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="336ab-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="336ab-110">Bir özellik değerini başka bir kaynaktan alınacağı özellik neden geçirilecek değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="336ab-111">Bu olarak bilinir *çevre*.</span><span class="sxs-lookup"><span data-stu-id="336ab-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="336ab-112">Bir özellik veya olay içinde görüntülenmesi gerekip gerekmediğini belirten bir **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="336ab-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="336ab-113">Grup özelliği veya görüntülenen olay kategorisi adını belirtir. bir <xref:System.Windows.Forms.PropertyGrid> denetim kümesine <xref:System.Windows.Forms.PropertySort.Categorized> modu.</span><span class="sxs-lookup"><span data-stu-id="336ab-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="336ab-114">Bir özellik için varsayılan değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="336ab-115">Bir özellik veya olay için bir açıklama belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="336ab-116">Bir özellik için görünen ad belirtir, olayı veya `public``void` bağımsız değişken almayan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="336ab-116">Specifies the display name for a property, event, or `public``void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="336ab-117">Bir özelliği değiştirmek için kullanılacak Düzenleyicisi'ni belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="336ab-118">Bir özellik veya yöntem bir düzenleyicide görüntülenebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="336ab-119">Bir sınıf veya üye bağlam anahtar sözcüğü belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="336ab-120">Bir özellik yerelleştirilmiş olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="336ab-121">Bir nesnenin metin gösterimi yıldızlar gibi karakterler tarafından getirilmemeli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="336ab-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="336ab-122">Bu öznitelik bağlı özelliği salt okunur veya okuma/yazma tasarım zamanında olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="336ab-123">İlişkili özelliğin değeri değiştiğinde özellik Kılavuzu yenilemelisiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="336ab-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="336ab-124">Bu öznitelik nesne için bir dönüştürücü kullanılacak türüne bağlı belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="336ab-125">Veri bağlama özellikleri için öznitelikler</span><span class="sxs-lookup"><span data-stu-id="336ab-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="336ab-126">Aşağıdaki tabloda özel denetimleri ve bileşenleri veri bağlama ile nasıl etkileşim belirtmek için uygulayabileceğiniz öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="336ab-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="336ab-127">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="336ab-127">Attribute</span></span>|<span data-ttu-id="336ab-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="336ab-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="336ab-129">Bir özelliği için bağlama genellikle kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="336ab-130">Bir bileşenin veri üye özellikleri ve veri kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="336ab-131">Bir bileşenin varsayılan bağlama özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="336ab-132">Bir bileşenin veri üye özellikleri ve veri kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="336ab-133">Yeniden yönlendirme etkinleştirir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="336ab-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="336ab-134">Sınıfları için öznitelikler</span><span class="sxs-lookup"><span data-stu-id="336ab-134">Attributes for Classes</span></span>  
 <span data-ttu-id="336ab-135">Aşağıdaki tabloda tasarım zamanında özel denetimleri ve bileşenleri davranışını belirtmek için uygulayabileceğiniz öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="336ab-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="336ab-136">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="336ab-136">Attribute</span></span>|<span data-ttu-id="336ab-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="336ab-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="336ab-138">Bir bileşen için varsayılan olayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="336ab-139">Bir bileşen için varsayılan özellik belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="336ab-140">Tasarım zamanı hizmetleri bileşeni için uygulamak için kullanılan sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="336ab-141">Tasarımcı bir sınıf için belirli bir kategoriye ait olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="336ab-142">Araç kutusu öğesi bir özniteliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="336ab-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="336ab-143">Araç kutusu öğesi için kullanmak üzere filtre türü ve filtre dizesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="336ab-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="336ab-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="336ab-144">See Also</span></span>  
 <xref:System.Attribute>  
 [<span data-ttu-id="336ab-145">Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="336ab-145">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="336ab-146">Tasarım zamanı desteği genişletme</span><span class="sxs-lookup"><span data-stu-id="336ab-146">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="336ab-147">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="336ab-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
