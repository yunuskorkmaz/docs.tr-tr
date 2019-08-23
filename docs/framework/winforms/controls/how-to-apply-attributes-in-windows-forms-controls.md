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
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922792"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="d6e46-102">Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="d6e46-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="d6e46-103">Tasarım ortamıyla doğru şekilde etkileşim kuran ve çalışma zamanında doğru şekilde yürütülen bileşenleri ve denetimleri geliştirmek için, öznitelikleri sınıflara ve üyelere doğru bir şekilde uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6e46-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6e46-104">Example</span></span>  
 <span data-ttu-id="d6e46-105">Aşağıdaki kod örneği, bir özel denetimde çeşitli özniteliklerin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="d6e46-106">Denetim, basit bir günlüğe kaydetme özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="d6e46-107">Denetim bir veri kaynağına bağlandığında, veri kaynağı tarafından bir <xref:System.Windows.Forms.DataGridView> denetimde gönderilen değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d6e46-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d6e46-108">Bir değer, `Threshold` özelliği tarafından belirtilen değeri aşarsa bir `ThresholdExceeded` olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="d6e46-109">Değerleri bir`LogEntry` sınıfıyla günlüğe kaydedilir. `AttributesDemoControl`</span><span class="sxs-lookup"><span data-stu-id="d6e46-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="d6e46-110">`LogEntry` Sınıfı, bir şablon sınıfıdır, bu, günlüğe kaydettiği tür üzerinde parametreleştirimiş olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="d6e46-111">Örneğin, Eğer `AttributesDemoControl` , türü `float`günlüğe kaydetme ise, her `LogEntry` örnek aşağıdaki şekilde bildirilmiştir ve kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6e46-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="d6e46-112">`LogEntry` , Rastgele bir tür tarafından parametrelendirildiği için, parametre türü üzerinde çalışması için yansıma kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="d6e46-113">Eşik özelliğinin çalışması için, parametre türünün `T` <xref:System.IComparable> arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="d6e46-114">Bir performans sayacını düzenli aralıklarla `AttributesDemoControl` sorgulayan form.</span><span class="sxs-lookup"><span data-stu-id="d6e46-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="d6e46-115">Her bir değer uygun bir `LogEntry` tür içinde paketlenmiştir ve <xref:System.Windows.Forms.BindingSource>formun öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="d6e46-116">, `AttributesDemoControl` Değeri veri bağlama aracılığıyla alır ve bir <xref:System.Windows.Forms.DataGridView> denetimdeki değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d6e46-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="d6e46-117">İlk kod örneği `AttributesDemoControl` uygulama.</span><span class="sxs-lookup"><span data-stu-id="d6e46-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="d6e46-118">İkinci kod örneği, `AttributesDemoControl`kullanan bir formu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="d6e46-119">Sınıf düzeyi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="d6e46-119">Class-level Attributes</span></span>  
 <span data-ttu-id="d6e46-120">Bazı öznitelikler sınıf düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d6e46-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="d6e46-121">Aşağıdaki kod örneği, bir Windows Forms denetimine yaygın olarak uygulanan öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="d6e46-122">TypeConverter özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6e46-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="d6e46-123"><xref:System.ComponentModel.TypeConverterAttribute>, başka bir yaygın kullanılan sınıf düzeyi özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="d6e46-124">Aşağıdaki kod örneği, `LogEntry` sınıfı için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="d6e46-125">Bu örnek ayrıca, olarak adlandırılan <xref:System.ComponentModel.TypeConverter> `LogEntry` `LogEntryTypeConverter`türü için bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="d6e46-126">Üye düzeyi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="d6e46-126">Member-level Attributes</span></span>  
 <span data-ttu-id="d6e46-127">Bazı öznitelikler üye düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d6e46-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="d6e46-128">Aşağıdaki kod örnekleri, Windows Forms denetimlerinin özelliklerine yaygın olarak uygulanan bazı öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="d6e46-129">AmbientValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6e46-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="d6e46-130">Aşağıdaki örnek öğesini gösterir <xref:System.ComponentModel.AmbientValueAttribute> ve tasarım ortamıyla etkileşimini destekleyen kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="d6e46-131">Bu etkileşime *Ambience*adı verilir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="d6e46-132">Veri bağlama öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="d6e46-132">Databinding Attributes</span></span>  
 <span data-ttu-id="d6e46-133">Aşağıdaki örneklerde karmaşık veri bağlamasının bir uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="d6e46-134">Daha önce gösterilen sınıf <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>düzeyi, veri bağlama için kullanılacak `DataSource` ve `DataMember` özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="d6e46-135">, <xref:System.ComponentModel.AttributeProviderAttribute> `DataSource` Özelliğin bağlanacağı türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d6e46-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d6e46-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="d6e46-137">Öğesini barındıran `AttributesDemoControl` form, derlemek için `AttributesDemoControl` derlemeye bir başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d6e46-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e46-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6e46-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="d6e46-139">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="d6e46-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="d6e46-140">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d6e46-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="d6e46-141">[Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="d6e46-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
