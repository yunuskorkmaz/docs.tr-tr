---
title: Denetimlere öznitelik uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: b8ecd516cf6bb189c6ad1b208dd8e3a5444f001c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741486"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="25d2e-102">Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="25d2e-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="25d2e-103">Tasarım ortamıyla doğru şekilde etkileşim kuran ve çalışma zamanında doğru şekilde yürütülen bileşenleri ve denetimleri geliştirmek için, öznitelikleri sınıflara ve üyelere doğru bir şekilde uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25d2e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="25d2e-104">Example</span></span>  
 <span data-ttu-id="25d2e-105">Aşağıdaki kod örneği, bir özel denetimde çeşitli özniteliklerin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="25d2e-106">Denetim, basit bir günlüğe kaydetme özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="25d2e-107">Denetim bir veri kaynağına bağlandığında, veri kaynağı tarafından gönderilen değerleri bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="25d2e-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="25d2e-108">Bir değer `Threshold` özelliği tarafından belirtilen değeri aşarsa `ThresholdExceeded` bir olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="25d2e-109">`AttributesDemoControl`, değerleri bir `LogEntry` sınıfıyla günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="25d2e-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="25d2e-110">`LogEntry` sınıfı bir şablon sınıfıdır ve bu, günlüğe kaydettiği tür üzerinde parametreleştirilenir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="25d2e-111">Örneğin, `AttributesDemoControl` `float`türündeki günlüğe kayıt alıyorsa, her `LogEntry` örnek aşağıdaki şekilde tanımlanır ve kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25d2e-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="25d2e-112">`LogEntry` rastgele bir tür tarafından parametrelendirildiği için, parametre türü üzerinde çalışmak üzere yansıma kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="25d2e-113">Eşik özelliğinin çalışması için `T` parametre türü <xref:System.IComparable> arabirimini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="25d2e-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="25d2e-114">`AttributesDemoControl` barındıran form, düzenli aralıklarla bir performans sayacını sorgular.</span><span class="sxs-lookup"><span data-stu-id="25d2e-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="25d2e-115">Her değer uygun türdeki bir `LogEntry` paketlenir ve formun <xref:System.Windows.Forms.BindingSource>eklenir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="25d2e-116">`AttributesDemoControl`, değeri veri bağlama aracılığıyla alır ve değeri bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="25d2e-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="25d2e-117">İlk kod örneği `AttributesDemoControl` uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="25d2e-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="25d2e-118">İkinci kod örneği, `AttributesDemoControl`kullanan bir formu gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="25d2e-119">Sınıf düzeyi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="25d2e-119">Class-level Attributes</span></span>  
 <span data-ttu-id="25d2e-120">Bazı öznitelikler sınıf düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="25d2e-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="25d2e-121">Aşağıdaki kod örneği, bir Windows Forms denetimine yaygın olarak uygulanan öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="25d2e-122">TypeConverter özniteliği</span><span class="sxs-lookup"><span data-stu-id="25d2e-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="25d2e-123"><xref:System.ComponentModel.TypeConverterAttribute>, yaygın olarak kullanılan bir sınıf düzeyi özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="25d2e-124">Aşağıdaki kod örneği, `LogEntry` sınıfı için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="25d2e-125">Bu örnek ayrıca `LogEntryTypeConverter`olarak adlandırılan `LogEntry` türü için <xref:System.ComponentModel.TypeConverter> bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="25d2e-126">Üye düzeyi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="25d2e-126">Member-level Attributes</span></span>  
 <span data-ttu-id="25d2e-127">Bazı öznitelikler üye düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="25d2e-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="25d2e-128">Aşağıdaki kod örnekleri, Windows Forms denetimlerinin özelliklerine yaygın olarak uygulanan bazı öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="25d2e-129">AmbientValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="25d2e-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="25d2e-130">Aşağıdaki örnek, <xref:System.ComponentModel.AmbientValueAttribute> gösterir ve tasarım ortamıyla etkileşimini destekleyen kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="25d2e-131">Bu etkileşime *Ambience*adı verilir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="25d2e-132">Veri bağlama öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="25d2e-132">Databinding Attributes</span></span>  
 <span data-ttu-id="25d2e-133">Aşağıdaki örneklerde karmaşık veri bağlamasının bir uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="25d2e-134">Daha önce gösterilen sınıf düzeyi <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, veri bağlama için kullanılacak `DataSource` ve `DataMember` özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="25d2e-135"><xref:System.ComponentModel.AttributeProviderAttribute>, `DataSource` özelliğinin bağlanacağı türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25d2e-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="25d2e-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="25d2e-137">`AttributesDemoControl` barındıran form, derlemek için `AttributesDemoControl` derlemesine bir başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="25d2e-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d2e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25d2e-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="25d2e-139">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="25d2e-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="25d2e-140">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25d2e-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="25d2e-141">[Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="25d2e-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
