---
title: BindingSource Bileşeni
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 0d07dc0ddf5e80d51d1494ff3398eeab150c3f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528164"
---
# <a name="bindingsource-component"></a><span data-ttu-id="99898-102">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="99898-102">BindingSource Component</span></span>
<span data-ttu-id="99898-103">Denetimlere bağlama için bir veri kaynağı yalıtır.</span><span class="sxs-lookup"><span data-stu-id="99898-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="99898-104"><xref:System.Windows.Forms.BindingSource> Bileşen iki amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="99898-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="99898-105">İlk olarak, bir form üzerinde denetimleri için veri bağlama sırasında yöneltme katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="99898-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="99898-106">Bu bağlama tarafından gerçekleştirilir <xref:System.Windows.Forms.BindingSource> veri kaynağınız ve formunuza denetimlere bağlama bileşen <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="99898-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="99898-107">Verilerle gezinme, sıralama, filtreleme ve güncelleştirilmesi de dahil olmak üzere tüm başka etkileşim çağrıları ile gerçekleştirilir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="99898-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="99898-108">İkinci, <xref:System.Windows.Forms.BindingSource> bileşen kesin türü belirtilmiş veri kaynağı olarak görev yapabilir.</span><span class="sxs-lookup"><span data-stu-id="99898-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="99898-109">Bir türe eklemek <xref:System.Windows.Forms.BindingSource> ile bileşen <xref:System.Windows.Forms.BindingSource.Add%2A> yöntemi bu tür bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99898-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99898-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="99898-110">In This Section</span></span>  
 [<span data-ttu-id="99898-111">BindingSource Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="99898-111">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 <span data-ttu-id="99898-112">Genel kavramlarını tanıtır <xref:System.Windows.Forms.BindingSource> bileşeni, bir veri kaynağı için bir denetim bağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="99898-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="99898-113">Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="99898-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="99898-114">Nasıl yapılacağını gösteren bir <xref:System.DBNull> kullanarak veri kaynağı değerden <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="99898-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="99898-115">Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="99898-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="99898-116">Kullanmayı göstermektedir <xref:System.Windows.Forms.BindingSource> uygulamak için bileşen sıralar ve görüntülenen verileri filtreler.</span><span class="sxs-lookup"><span data-stu-id="99898-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="99898-117">Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama</span><span class="sxs-lookup"><span data-stu-id="99898-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="99898-118">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.BindingSource> bir Web hizmetine bağlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="99898-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="99898-119">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="99898-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="99898-120">Kullanmayı göstermektedir <xref:System.Windows.Forms.BindingSource> düzgün biçimde bir veri bağlama işleminde ortaya çıkan hataları işlemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="99898-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="99898-121">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="99898-121">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="99898-122">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> bir türe Bağlama bileşeni.</span><span class="sxs-lookup"><span data-stu-id="99898-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="99898-123">Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama</span><span class="sxs-lookup"><span data-stu-id="99898-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="99898-124">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> üretecini veya yöntem bağlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="99898-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="99898-125">Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="99898-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="99898-126">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> yeni öğeler oluşturabilir ve bunları bir veri kaynağına eklemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="99898-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="99898-127">Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="99898-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="99898-128">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> desteklemeyen veri kaynakları bildirimi değiştirmek için değişiklik bildirimi olayları yükseltmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="99898-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="99898-129">Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="99898-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="99898-130">Öğesinden devralan bir tür kullanımı gösterilmiştir <xref:System.ComponentModel.INotifyPropertyChanged> ile bir <xref:System.Windows.Forms.BindingSource> denetim.</span><span class="sxs-lookup"><span data-stu-id="99898-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="99898-131">Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma</span><span class="sxs-lookup"><span data-stu-id="99898-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="99898-132">Veri kaynağı kullanarak değişikliklerine yanıt verme gösterilmiştir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="99898-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="99898-133">Nasıl Yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma</span><span class="sxs-lookup"><span data-stu-id="99898-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="99898-134">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.BindingSource> birden çok form aynı veri kaynağına bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="99898-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="99898-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="99898-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="99898-136">Başvuru belgelerine sağlar <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="99898-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="99898-137">Başvuru belgelerine sağlar <xref:System.Windows.Forms.BindingNavigator> denetim.</span><span class="sxs-lookup"><span data-stu-id="99898-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99898-138">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="99898-138">Related Sections</span></span>  
 [<span data-ttu-id="99898-139">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="99898-139">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="99898-140">Windows Forms veri bağlama mimarisi açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="99898-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="99898-141">Ayrıca bkz. [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="99898-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
