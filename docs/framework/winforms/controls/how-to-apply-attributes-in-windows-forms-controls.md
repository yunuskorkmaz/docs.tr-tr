---
title: 'Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 49c2aaa48a48e33a71b5112db31991975011551d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529642"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="b3af2-102">Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="b3af2-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="b3af2-103">Bileşenleri ve doğru tasarım ortamı ile etkileşim ve doğru şekilde çalışma zamanında yürütmek denetimleri geliştirmek için sınıflar ve üyeleri öznitelikleri doğru uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3af2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3af2-104">Example</span></span>  
 <span data-ttu-id="b3af2-105">Aşağıdaki kod örneğinde, özel bir denetim birkaç öznitelik kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="b3af2-106">Denetim basit günlük özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="b3af2-107">Denetim bir veri kaynağına bağlandığında, veri kaynağında gönderdiği değerlerini görüntüler bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="b3af2-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b3af2-108">Bir değer tarafından belirtilen değeri aşarsa `Threshold` özelliği, bir `ThresholdExceeded` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3af2-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="b3af2-109">`AttributesDemoControl` Değerlerle günlüklerini bir `LogEntry` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b3af2-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="b3af2-110">`LogEntry` , Bu günlükleri türüne parametreli anlamına gelir bir şablon sınıfı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b3af2-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="b3af2-111">Örneğin, varsa `AttributesDemoControl` günlük türü değerleri olan `float`, her `LogEntry` örneği bildirilir ve aşağıdaki gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3af2-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="b3af2-112">Çünkü `LogEntry` parametrelenmiş rasgele bir türe göre onu yansıma parametre türü üzerinde çalışması için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="b3af2-113">Eşik özelliğinin çalışması, parametre türü `T` uygulamalıdır <xref:System.IComparable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b3af2-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="b3af2-114">Barındıran form `AttributesDemoControl` bir performans sayacı düzenli aralıklarla sorgular.</span><span class="sxs-lookup"><span data-stu-id="b3af2-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="b3af2-115">Her değer paketlenmiştir bir `LogEntry` uygun türde ve formun eklenen <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="b3af2-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="b3af2-116">`AttributesDemoControl` Değeri, veri bağlama aracılığıyla alır ve değerini görüntüler bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="b3af2-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="b3af2-117">İlk bir kod örneğidir `AttributesDemoControl` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="b3af2-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="b3af2-118">İkinci kod örneğinde kullanan bir form gösterilmektedir `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="b3af2-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="b3af2-119">Sınıf düzeyi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3af2-119">Class-level Attributes</span></span>  
 <span data-ttu-id="b3af2-120">Bazı öznitelikler sınıf düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b3af2-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="b3af2-121">Aşağıdaki kod örneği, bir Windows Forms denetimi için yaygın olarak uygulanan öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="b3af2-122">Typeconverter'a özniteliği</span><span class="sxs-lookup"><span data-stu-id="b3af2-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="b3af2-123"><xref:System.ComponentModel.TypeConverterAttribute> başka bir yaygın olarak kullanılan sınıf düzeyi özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="b3af2-124">Aşağıdaki kod örneği, kullanım için gösterir `LogEntry` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b3af2-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="b3af2-125">Bu örnek ayrıca uygulaması gösterir bir <xref:System.ComponentModel.TypeConverter> için `LogEntry` adlı türü `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="b3af2-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="b3af2-126">Üye düzeyi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3af2-126">Member-level Attributes</span></span>  
 <span data-ttu-id="b3af2-127">Bazı öznitelikler üye düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b3af2-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="b3af2-128">Aşağıdaki kod örnekleri, yaygın olarak Windows Forms denetimleri özelliklerine uygulanan bazı öznitelikler gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="b3af2-129">AmbientValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="b3af2-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="b3af2-130">Aşağıdaki örnekte gösterilmiştir <xref:System.ComponentModel.AmbientValueAttribute> ve tasarım ortamı ile etkileşimi destekler kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="b3af2-131">Bu etkileşimi adlı *çevre*.</span><span class="sxs-lookup"><span data-stu-id="b3af2-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="b3af2-132">Veri bağlama öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3af2-132">Databinding Attributes</span></span>  
 <span data-ttu-id="b3af2-133">Aşağıdaki örnekler, karmaşık veri bağlama uygulaması göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b3af2-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="b3af2-134">Sınıf düzeyi <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>gösterilen daha önce belirtir `DataSource` ve `DataMember` veri bağlaması için kullanılacak özellikler.</span><span class="sxs-lookup"><span data-stu-id="b3af2-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="b3af2-135"><xref:System.ComponentModel.AttributeProviderAttribute> Türün belirtir `DataSource` özelliğini bağlayın.</span><span class="sxs-lookup"><span data-stu-id="b3af2-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3af2-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b3af2-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b3af2-137">Barındıran form `AttributesDemoControl` başvuru gerektirir `AttributesDemoControl` oluşturmak için derleme.</span><span class="sxs-lookup"><span data-stu-id="b3af2-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3af2-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3af2-138">See Also</span></span>  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="b3af2-139">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="b3af2-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="b3af2-140">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3af2-140">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="b3af2-141">Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale</span><span class="sxs-lookup"><span data-stu-id="b3af2-141">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
