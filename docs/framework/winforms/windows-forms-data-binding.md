---
title: Veri Bağlama
description: Formdaki denetimlerde veri kaynağındaki bilgileri göstermek ve üzerinde değişiklik yapmak için Windows Forms ' de veri bağlamayı nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325545"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="0a59a-103">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="0a59a-103">Windows Forms Data Binding</span></span>
<span data-ttu-id="0a59a-104">Windows Forms veri bağlama, formdaki denetimlerde bir veri kaynağından bilgi görüntüleme ve değişiklik yapma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-104">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="0a59a-105">Hem geleneksel veri kaynaklarına hem de veri içeren neredeyse her yapıya bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a59a-105">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a59a-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0a59a-106">In This Section</span></span>  
 [<span data-ttu-id="0a59a-107">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0a59a-107">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="0a59a-108">Windows Forms 'de veri bağlamaya genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-108">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="0a59a-109">Windows Forms Tarafından Desteklenen Veri Kaynakları</span><span class="sxs-lookup"><span data-stu-id="0a59a-109">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="0a59a-110">Windows Forms ile kullanılabilecek veri kaynaklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-110">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="0a59a-111">Veri Bağlama ile İlgili Arabirimler</span><span class="sxs-lookup"><span data-stu-id="0a59a-111">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="0a59a-112">Windows Forms veri bağlama ile kullanılan birçok arabirimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-112">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="0a59a-113">Nasıl yapılır: Windows Forms Verilerinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="0a59a-113">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="0a59a-114">Bir veri kaynağındaki öğelerde nasıl gezinirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a59a-114">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="0a59a-115">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0a59a-115">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="0a59a-116">Windows Forms veri bağlama için farklı değişiklik bildirimi türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-116">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="0a59a-117">Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="0a59a-117">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="0a59a-118">Arabirimin nasıl uygulanacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> .</span><span class="sxs-lookup"><span data-stu-id="0a59a-118">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="0a59a-119">Arabirim, bir iş nesnesindeki özellik değişikliklerinin bağlı bir denetime iletişim kurar</span><span class="sxs-lookup"><span data-stu-id="0a59a-119">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="0a59a-120">Nasıl yapılır: PropertyNameChanged Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="0a59a-120">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="0a59a-121">Windows Forms Kullanıcı denetiminin özelliklerine *PropertyName*değiştirilmiş deseninin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a59a-121">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="0a59a-122">Nasıl yapılır: ITypedList Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="0a59a-122">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="0a59a-123">Arabirimi uygulayarak, bağlanabilir bir liste için şemanın keşfinin nasıl etkinleştirileceğini gösterir <xref:System.ComponentModel.ITypedList> .</span><span class="sxs-lookup"><span data-stu-id="0a59a-123">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="0a59a-124">Nasıl yapılır: IListSource Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="0a59a-124">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="0a59a-125"><xref:System.ComponentModel.IListSource>Bağlanabilir bir sınıf oluşturmak için arabirimin nasıl uygulanacağını gösterir <xref:System.Collections.IList> , ancak başka bir konumdan liste sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-125">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="0a59a-126">Nasıl yapılır: Aynı Veri Kaynağına Bağlanan Birden Çok Denetimin Eşitlenmiş Kalmasını Sağlama</span><span class="sxs-lookup"><span data-stu-id="0a59a-126">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="0a59a-127"><xref:System.Windows.Forms.BindingSource.BindingComplete>Bir veri kaynağıyla bağlantılı tüm denetimlerin eşitlenmiş olarak kalmasını sağlamak için olayın nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a59a-127">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="0a59a-128">Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama</span><span class="sxs-lookup"><span data-stu-id="0a59a-128">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="0a59a-129">Üst tablodaki bir alanda değişiklik yapıldığında bir alt tablonun seçili satırının değişmediğinden nasıl emin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a59a-129">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="0a59a-130">Ayrıca bkz. [veri bağlama](interfaces-related-to-data-binding.md), [nasıl yapılır: Windows Forms verilerde gezinme](how-to-navigate-data-in-windows-forms.md)ve [nasıl yapılır: bir Windows formunda basit bağlantılı denetim oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="0a59a-130">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0a59a-131">Başvuru</span><span class="sxs-lookup"><span data-stu-id="0a59a-131">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="0a59a-132">Bağlanabilir bir bileşen ve bir veri kaynağı arasındaki bağlamayı temsil eden sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-132">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="0a59a-133">Denetimlere bağlamak için bir veri kaynağını kapsülleyen sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-133">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a59a-134">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0a59a-134">Related Sections</span></span>  
 [<span data-ttu-id="0a59a-135">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="0a59a-135">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="0a59a-136">Bileşenin nasıl kullanılacağını gösteren konuların bir listesini içerir <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="0a59a-136">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="0a59a-137">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="0a59a-137">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="0a59a-138">Bağlanabilir DataGrid denetiminin nasıl kullanılacağını gösteren konuların bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a59a-138">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="0a59a-139">Ayrıca bkz. [Visual Studio 'Da verilere erişme](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="0a59a-139">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
