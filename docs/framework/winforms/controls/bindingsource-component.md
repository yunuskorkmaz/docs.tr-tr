---
title: "BindingSource Bileşeni"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 006cafafdf8e3c3f4da77394d6155fa52e113b58
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="bindingsource-component"></a><span data-ttu-id="6f908-102">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="6f908-102">BindingSource Component</span></span>
<span data-ttu-id="6f908-103">Denetimlere bağlama için bir veri kaynağı yalıtır.</span><span class="sxs-lookup"><span data-stu-id="6f908-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="6f908-104"><xref:System.Windows.Forms.BindingSource> Bileşen iki amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="6f908-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="6f908-105">İlk olarak, bir form üzerinde denetimleri için veri bağlama sırasında yöneltme katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f908-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="6f908-106">Bu bağlama tarafından gerçekleştirilir <xref:System.Windows.Forms.BindingSource> veri kaynağınız ve formunuza denetimlere bağlama bileşen <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6f908-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="6f908-107">Verilerle gezinme, sıralama, filtreleme ve güncelleştirilmesi de dahil olmak üzere tüm başka etkileşim çağrıları ile gerçekleştirilir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6f908-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="6f908-108">İkinci, <xref:System.Windows.Forms.BindingSource> bileşen kesin türü belirtilmiş veri kaynağı olarak görev yapabilir.</span><span class="sxs-lookup"><span data-stu-id="6f908-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="6f908-109">Bir türe eklemek <xref:System.Windows.Forms.BindingSource> ile bileşen <xref:System.Windows.Forms.BindingSource.Add%2A> yöntemi bu tür bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f908-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f908-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6f908-110">In This Section</span></span>  
 [<span data-ttu-id="6f908-111">BindingSource bileşenine genel bakış</span><span class="sxs-lookup"><span data-stu-id="6f908-111">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 <span data-ttu-id="6f908-112">Genel kavramlarını tanıtır <xref:System.Windows.Forms.BindingSource> bileşeni, bir veri kaynağı için bir denetim bağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f908-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="6f908-113">Nasıl yapılır: Windows Forms denetimlerini DBNull veritabanı değerlerine bağlama</span><span class="sxs-lookup"><span data-stu-id="6f908-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="6f908-114">Nasıl yapılacağını gösteren bir <xref:System.DBNull> kullanarak veri kaynağı değerden <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6f908-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="6f908-115">Nasıl yapılır: Windows Forms BindingSource bileşeni ile ADO.NET verilerini sıralama ve filtreleme</span><span class="sxs-lookup"><span data-stu-id="6f908-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="6f908-116">Kullanmayı göstermektedir <xref:System.Windows.Forms.BindingSource> uygulamak için bileşen sıralar ve görüntülenen verileri filtreler.</span><span class="sxs-lookup"><span data-stu-id="6f908-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="6f908-117">Nasıl yapılır: Windows Forms BindingSource ile bir Web hizmetine bağlama</span><span class="sxs-lookup"><span data-stu-id="6f908-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="6f908-118">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.BindingSource> bir Web hizmetine bağlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="6f908-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="6f908-119">Nasıl yapılır: hatalar ve oluşan özel durumlar Veri bağlamada işleme</span><span class="sxs-lookup"><span data-stu-id="6f908-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="6f908-120">Kullanmayı göstermektedir <xref:System.Windows.Forms.BindingSource> düzgün biçimde bir veri bağlama işleminde ortaya çıkan hataları işlemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="6f908-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="6f908-121">Nasıl yapılır: Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="6f908-121">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="6f908-122">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> bir türe Bağlama bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6f908-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="6f908-123">Nasıl yapılır: Windows Forms denetimini bir Fabrika nesnesine bağlama</span><span class="sxs-lookup"><span data-stu-id="6f908-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="6f908-124">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> üretecini veya yöntem bağlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="6f908-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="6f908-125">Nasıl yapılır: Windows Forms BindingSource ile öğe eklemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6f908-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="6f908-126">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> yeni öğeler oluşturabilir ve bunları bir veri kaynağına eklemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="6f908-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="6f908-127">Nasıl yapılır: BindingSource Resetıtem yöntemini kullanarak değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="6f908-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="6f908-128">Kullanarak gösteren bir <xref:System.Windows.Forms.BindingSource> desteklemeyen veri kaynakları bildirimi değiştirmek için değişiklik bildirimi olayları yükseltmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="6f908-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="6f908-129">Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="6f908-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="6f908-130">Öğesinden devralan bir tür kullanımı gösterilmiştir <xref:System.ComponentModel.INotifyPropertyChanged> ile bir <xref:System.Windows.Forms.BindingSource> denetim.</span><span class="sxs-lookup"><span data-stu-id="6f908-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="6f908-131">Nasıl yapılır: BindingSource ile Windows Forms denetiminde veri kaynağı güncelleştirmelerini yansıtma</span><span class="sxs-lookup"><span data-stu-id="6f908-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="6f908-132">Veri kaynağı kullanarak değişikliklerine yanıt verme gösterilmiştir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6f908-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="6f908-133">Nasıl yapılır: bağlı veri BindingSource bileşenini kullanarak formlar arasında paylaşma</span><span class="sxs-lookup"><span data-stu-id="6f908-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="6f908-134">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.BindingSource> birden çok form aynı veri kaynağına bağlanamadı.</span><span class="sxs-lookup"><span data-stu-id="6f908-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6f908-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6f908-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="6f908-136">Başvuru belgelerine sağlar <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6f908-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="6f908-137">Başvuru belgelerine sağlar <xref:System.Windows.Forms.BindingNavigator> denetim.</span><span class="sxs-lookup"><span data-stu-id="6f908-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f908-138">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6f908-138">Related Sections</span></span>  
 [<span data-ttu-id="6f908-139">Windows Forms veri bağlama</span><span class="sxs-lookup"><span data-stu-id="6f908-139">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="6f908-140">Windows Forms veri bağlama mimarisi açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="6f908-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="6f908-141">Ayrıca bkz. [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6f908-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
