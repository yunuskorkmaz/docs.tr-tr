---
title: Windows Forms Veri Bağlama
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: ed456807137e8cf7594bc50eb0eebb67b88e6b40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704615"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="6e00e-102">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="6e00e-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="6e00e-103">Windows Forms veri bağlama görüntülemek ve form üzerinde denetimleri bir veri kaynağından bilgi değişiklikler yapmanız için Araçlar verir.</span><span class="sxs-lookup"><span data-stu-id="6e00e-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="6e00e-104">Hem geleneksel veri kaynakları yanı sıra veri içeren neredeyse tüm yapısı bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e00e-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e00e-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6e00e-105">In This Section</span></span>  
 [<span data-ttu-id="6e00e-106">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e00e-106">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="6e00e-107">Windows Forms veri bağlama genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e00e-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="6e00e-108">Windows Forms Tarafından Desteklenen Veri Kaynakları</span><span class="sxs-lookup"><span data-stu-id="6e00e-108">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="6e00e-109">Windows Forms ile kullanılabilen veri kaynaklarını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e00e-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="6e00e-110">Veri Bağlama ile İlgili Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6e00e-110">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="6e00e-111">Windows Forms veri bağlama ile kullanılan arabirimlerin bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e00e-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="6e00e-112">Nasıl yapılır: Windows Forms'ta verilerde gezinme</span><span class="sxs-lookup"><span data-stu-id="6e00e-112">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="6e00e-113">Bir veri kaynağındaki öğeleri arasında gezinmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e00e-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="6e00e-114">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6e00e-114">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="6e00e-115">Windows Forms veri bağlama için değişiklik bildirimi farklı türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e00e-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="6e00e-116">Nasıl yapılır: INotifyPropertyChanged arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="6e00e-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="6e00e-117">Nasıl uygulayacağınızı gösteren <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6e00e-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="6e00e-118">Arabirim ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerinin iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="6e00e-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="6e00e-119">Nasıl yapılır: PropertyNameChanged desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="6e00e-119">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="6e00e-120">Nasıl uygulanacağını gösterir *PropertyName*bir Windows Forms kullanıcı denetimi özelliklerini değiştirilen deseni.</span><span class="sxs-lookup"><span data-stu-id="6e00e-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="6e00e-121">Nasıl yapılır: Itypedlist arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="6e00e-121">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="6e00e-122">Uygulayarak bağlanabilir bir listesi için şema bulunmasını etkinleştirmek gösterilmektedir <xref:System.ComponentModel.ITypedList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6e00e-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="6e00e-123">Nasıl yapılır: IListSource arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="6e00e-123">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="6e00e-124">Nasıl uygulayacağınızı gösteren <xref:System.ComponentModel.IListSource> bağlanabilir bir sınıf oluşturmak için arabirimi uygulamıyor <xref:System.Collections.IList>, ancak başka bir konumdan bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e00e-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="6e00e-125">Nasıl yapılır: Birden çok denetimin eşitlenmiş kalmasını aynı veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="6e00e-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="6e00e-126">Nasıl işleneceğini gösterir <xref:System.Windows.Forms.BindingSource.BindingComplete> olay bir veri kaynağına bağlı tüm denetimleri eşitlenmiş kalmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="6e00e-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="6e00e-127">Nasıl yapılır: Bir alt tabloda seçilen satırın doğru konumda kalmasını sağlama</span><span class="sxs-lookup"><span data-stu-id="6e00e-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="6e00e-128">Üst tablo alanı için bir değişiklik yapıldığında, bir alt tabloda seçilen satırı değişmez emin olmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e00e-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="6e00e-129">Ayrıca bkz: [arabirimleri ilgili veri bağlama için](interfaces-related-to-data-binding.md), [nasıl yapılır: Windows Forms'ta verilerde gezinme](how-to-navigate-data-in-windows-forms.md), ve [nasıl yapılır: Bir Windows formunda basit bağlantılı denetim oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="6e00e-129">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6e00e-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6e00e-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="6e00e-131">Bağlanabilir bir bileşeni ve bir veri kaynağı arasındaki bağlamayı temsil eden sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6e00e-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="6e00e-132">Denetimlere bağlama için bir veri kaynağı kapsülleyen sınıftır açıklar.</span><span class="sxs-lookup"><span data-stu-id="6e00e-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6e00e-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6e00e-133">Related Sections</span></span>  
 [<span data-ttu-id="6e00e-134">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="6e00e-134">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="6e00e-135">Nasıl kullanılacağını gösteren konuların listesini içeren <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6e00e-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="6e00e-136">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="6e00e-136">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="6e00e-137">Bağlanabilir datagrid denetimine nasıl kazandırabileceğinizi konuların listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e00e-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="6e00e-138">Ayrıca bkz: [Visual Studio'da verilere erişme](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6e00e-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
