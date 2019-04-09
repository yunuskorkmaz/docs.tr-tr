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
ms.openlocfilehash: e86277c06e515b28bada3331cf4fd63e536319a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079597"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="9aa2f-102">Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="9aa2f-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="9aa2f-103">Bileşen ve Denetim doğru tasarım ortamı ile etkileşimli ve düzgün çalışma zamanında yürüten geliştirmek için öznitelikleri doğru sınıflar ve üyeler uygulama gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aa2f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aa2f-104">Example</span></span>  
 <span data-ttu-id="9aa2f-105">Aşağıdaki kod örneği, çeşitli öznitelikler özel bir denetimi kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="9aa2f-106">Denetim, bir basit günlüğe kaydetme özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="9aa2f-107">Denetim bir veri kaynağına bağlandığında, veri kaynağında tarafından gönderilen değerlerini görüntüler. bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9aa2f-108">Bir değeri tarafından belirtilen değeri aşarsa `Threshold` özelliği, bir `ThresholdExceeded` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="9aa2f-109">`AttributesDemoControl` Değerlerle günlükleri bir `LogEntry` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="9aa2f-110">`LogEntry` , Bu günlükleri türüne parametreli anlamına gelir. bir şablon sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="9aa2f-111">Örneğin, varsa `AttributesDemoControl` günlük değerler türü `float`, her `LogEntry` örneği bildirildi ve şu şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="9aa2f-112">Çünkü `LogEntry` parametrelenmiş bir rastgele türüne göre bu yansıma parametre türü üzerinde çalışılacak kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="9aa2f-113">Eşik özelliğin çalışması, parametre türü `T` uygulamalıdır <xref:System.IComparable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="9aa2f-114">Barındıran formun `AttributesDemoControl` bir performans sayacı düzenli aralıklarla sorgular.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="9aa2f-115">Her değer, paketlenmiş bir `LogEntry` uygun türde ve formun eklenen <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="9aa2f-116">`AttributesDemoControl` Değeri kendi veri bağlama aracılığıyla alır ve değerini görüntüler bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="9aa2f-117">İlk kod örnektir `AttributesDemoControl` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="9aa2f-118">İkinci kod örneğinde kullanan bir form gösterir `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="9aa2f-119">Sınıf düzeyinde öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9aa2f-119">Class-level Attributes</span></span>  
 <span data-ttu-id="9aa2f-120">Bazı öznitelikler sınıf düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="9aa2f-121">Aşağıdaki kod örneği, bir Windows Forms denetimi için yaygın olarak uygulanan öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="9aa2f-122">Atribut TypeConverter</span><span class="sxs-lookup"><span data-stu-id="9aa2f-122">TypeConverter Attribute</span></span>  
 <xref:System.ComponentModel.TypeConverterAttribute> <span data-ttu-id="9aa2f-123">başka bir yaygın olarak kullanılan sınıf düzeyi özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-123">is another commonly used class-level attribute.</span></span> <span data-ttu-id="9aa2f-124">Aşağıdaki kod örneği, uygunsa kullanımını gösterir `LogEntry` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="9aa2f-125">Bu örnek ayrıca uygulanışı gösterilmektedir bir <xref:System.ComponentModel.TypeConverter> için `LogEntry` adlı türü `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="9aa2f-126">Üye düzeyinde öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9aa2f-126">Member-level Attributes</span></span>  
 <span data-ttu-id="9aa2f-127">Bazı öznitelikler üye düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="9aa2f-128">Aşağıdaki kod örnekleri Windows Forms denetimlerindeki özellikler için yaygın olarak uygulanan bazı öznitelikler gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="9aa2f-129">AmbientValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="9aa2f-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="9aa2f-130">Aşağıdaki örnek, gösterir <xref:System.ComponentModel.AmbientValueAttribute> ve tasarım ortamı ile etkileşimi destekleyen ilişkili kodları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="9aa2f-131">Bu etkileşimi adlı *çevre*.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="9aa2f-132">Veri bağlama öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="9aa2f-132">Databinding Attributes</span></span>  
 <span data-ttu-id="9aa2f-133">Aşağıdaki örnekler, karmaşık veri bağlama uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="9aa2f-134">Sınıf düzeyi <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>gösterilen önceden belirtir `DataSource` ve `DataMember` kullanmak için veri bağlama özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="9aa2f-135"><xref:System.ComponentModel.AttributeProviderAttribute> Türün belirtir `DataSource` bağlama özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9aa2f-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9aa2f-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="9aa2f-137">Barındıran formun `AttributesDemoControl` başvurusu gerektirir `AttributesDemoControl` oluşturmak için derleme.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa2f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aa2f-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="9aa2f-139">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="9aa2f-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9aa2f-140">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9aa2f-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="9aa2f-141">Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9aa2f-141">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
