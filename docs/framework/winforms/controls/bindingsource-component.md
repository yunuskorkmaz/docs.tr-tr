---
title: BindingSource Bileşeni
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683424"
---
# <a name="bindingsource-component"></a><span data-ttu-id="b44ac-102">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="b44ac-102">BindingSource Component</span></span>
<span data-ttu-id="b44ac-103">Denetimlere bağlama için bir veri kaynağı kapsüller.</span><span class="sxs-lookup"><span data-stu-id="b44ac-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="b44ac-104"><xref:System.Windows.Forms.BindingSource> Bileşen iki amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="b44ac-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="b44ac-105">İlk olarak, bir form üzerinde denetimleri için veri bağlama sırasında bir yöneltme katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b44ac-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="b44ac-106">Bu bağlama tarafından gerçekleştirilir <xref:System.Windows.Forms.BindingSource> veri kaynağınızı ve ardından formunuza denetimlere bağlama bileşen <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b44ac-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b44ac-107">Tüm başka gezinme, sıralama, filtreleme ve güncelleştirme de dahil olmak üzere veri etkileşim çağrılarıyla gerçekleştirilir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b44ac-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="b44ac-108">İkinci olarak, <xref:System.Windows.Forms.BindingSource> bileşeni, kesin türü belirtilmiş veri kaynağı olarak hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="b44ac-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="b44ac-109">Bir türe eklemek <xref:System.Windows.Forms.BindingSource> ile bileşen <xref:System.Windows.Forms.BindingSource.Add%2A> yöntem o türün bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b44ac-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b44ac-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b44ac-110">In This Section</span></span>  
 [<span data-ttu-id="b44ac-111">BindingSource Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b44ac-111">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)  
 <span data-ttu-id="b44ac-112">Genel konseptlerini tanıtan <xref:System.Windows.Forms.BindingSource> bir denetimi veri kaynağına bağlamak izin veren bir bileşen.</span><span class="sxs-lookup"><span data-stu-id="b44ac-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="b44ac-113">Nasıl yapılır: Windows Forms denetimlerini DBNull veritabanı değerlerine bağlama</span><span class="sxs-lookup"><span data-stu-id="b44ac-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="b44ac-114">Nasıl yapılacağını gösteren bir <xref:System.DBNull> kullanarak veri kaynağına değerden <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b44ac-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="b44ac-115">Nasıl yapılır: Windows ile ADO.NET verilerini sıralama ve filtreleme Forms BindingSource bileşeni</span><span class="sxs-lookup"><span data-stu-id="b44ac-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="b44ac-116">Kullanmayı gösterir <xref:System.Windows.Forms.BindingSource> uygulamak için bileşen sıralar ve filtreler için görüntülenen verileri.</span><span class="sxs-lookup"><span data-stu-id="b44ac-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="b44ac-117">Nasıl yapılır: Windows Forms BindingSource ile bir Web hizmetine bağlama</span><span class="sxs-lookup"><span data-stu-id="b44ac-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="b44ac-118">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.BindingSource> bir Web hizmetine bağlama için bileşen.</span><span class="sxs-lookup"><span data-stu-id="b44ac-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="b44ac-119">Nasıl yapılır: Hataları ve ortaya çıkan özel durumlar veri bağlama ile işleme</span><span class="sxs-lookup"><span data-stu-id="b44ac-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="b44ac-120">Kullanmayı gösterir <xref:System.Windows.Forms.BindingSource> bileşeni düzgün bir şekilde bir veri bağlama işleminde ortaya çıkan hataları işlemek için.</span><span class="sxs-lookup"><span data-stu-id="b44ac-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="b44ac-121">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="b44ac-121">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="b44ac-122">Kullanmayı gösterir bir <xref:System.Windows.Forms.BindingSource> bir türe bağlama için bileşen.</span><span class="sxs-lookup"><span data-stu-id="b44ac-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="b44ac-123">Nasıl yapılır: Bir Windows Forms denetimini bir Fabrika nesnesine bağlama</span><span class="sxs-lookup"><span data-stu-id="b44ac-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="b44ac-124">Kullanmayı gösterir bir <xref:System.Windows.Forms.BindingSource> bir Fabrika nesnesine veya yöntemi bağlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="b44ac-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="b44ac-125">Nasıl yapılır: Windows Forms BindingSource ile öğe eklemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b44ac-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="b44ac-126">Kullanmayı gösterir bir <xref:System.Windows.Forms.BindingSource> yeni öğeleri oluşturun ve bunları bir veri kaynağına eklemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="b44ac-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="b44ac-127">Nasıl yapılır: BindingSource ve Resetıtem metodunu kullanarak değişiklik bildirimleri Yükselt</span><span class="sxs-lookup"><span data-stu-id="b44ac-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="b44ac-128">Kullanmayı gösterir bir <xref:System.Windows.Forms.BindingSource> değişikliği bildirimi desteklemeyen veri kaynakları değişiklik bildirimi olayları yükseltmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="b44ac-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="b44ac-129">Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri Yükselt</span><span class="sxs-lookup"><span data-stu-id="b44ac-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="b44ac-130">Öğesinden devralan bir tür gösterir <xref:System.ComponentModel.INotifyPropertyChanged> ile bir <xref:System.Windows.Forms.BindingSource> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b44ac-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="b44ac-131">Nasıl yapılır: BindingSource ile Windows Forms denetiminde veri kaynağı güncelleştirmelerini yansıtma</span><span class="sxs-lookup"><span data-stu-id="b44ac-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="b44ac-132">Veri kaynağı kullanarak değişikliklerine yanıt verme gösterilmektedir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b44ac-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="b44ac-133">Nasıl yapılır: Bağlı veri BindingSource bileşenini kullanarak formlar arasında paylaşma</span><span class="sxs-lookup"><span data-stu-id="b44ac-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="b44ac-134">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.BindingSource> birden çok form aynı veri kaynağına bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="b44ac-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b44ac-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b44ac-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="b44ac-136">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b44ac-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="b44ac-137">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.BindingNavigator> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b44ac-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b44ac-138">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b44ac-138">Related Sections</span></span>  
 [<span data-ttu-id="b44ac-139">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="b44ac-139">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="b44ac-140">Windows Forms veri bağlama mimarisi açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b44ac-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="b44ac-141">Ayrıca bkz: [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b44ac-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
