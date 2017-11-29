---
title: "Bağlam düzenleme ModelItem kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fde8bf45e01f8e3fede04c08d63177271a4a6faf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="191d7-102">Bağlam düzenleme ModelItem kullanma</span><span class="sxs-lookup"><span data-stu-id="191d7-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="191d7-103"><xref:System.Activities.Presentation.Model.ModelItem> Bağlam düzenleme nesnedir, konak uygulama Tasarımcısı ile iletişim kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="191d7-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="191d7-104"><xref:System.Activities.Presentation.EditingContext>iki yöntem sunar <xref:System.Activities.Presentation.EditingContext.Items%2A> ve <xref:System.Activities.Presentation.EditingContext.Services%2A>, kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="191d7-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="191d7-105">Öğeleri koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="191d7-105">The Items collection</span></span>  
 <span data-ttu-id="191d7-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Koleksiyonu Tasarımcısı ve ana bilgisayar arasında paylaşılan veri veya tüm tasarımcıları için kullanılabilir veri erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="191d7-107">Bu koleksiyon üzerinden erişilen aşağıdaki özellikleri içerir <xref:System.Activities.Presentation.ContextItemManager> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="191d7-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="191d7-108">Hizmetler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="191d7-108">The Services collection</span></span>  
 <span data-ttu-id="191d7-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Koleksiyonu Tasarımcı konak ile etkileşim kurmak için kullandığı hizmetleri veya tüm tasarımcıları hizmetine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="191d7-110">Bu koleksiyon Not aşağıdaki yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="191d7-110">This collection has the following methods of note:</span></span>  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="191d7-111">Bir etkinlik bir tasarımcı atama</span><span class="sxs-lookup"><span data-stu-id="191d7-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="191d7-112">Bir etkinliği kullanan hangi Tasarımcısı belirtmek için tasarımcı özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="191d7-113">Bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="191d7-113">Creating a service</span></span>  
 <span data-ttu-id="191d7-114">Tasarımcı ve ana bilgisayar arasındaki bilgi conduit görevi gören bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="191d7-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="191d7-115">Arabirim tarafından kullanılan <xref:System.Activities.Presentation.ServiceManager.Publish%2A> hizmet ve uygulama üyelerini tanımlamak üzere yöntemi hizmeti için mantık içerir.</span><span class="sxs-lookup"><span data-stu-id="191d7-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="191d7-116">Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="191d7-116">In the following code example, a service interface and implementation are created.</span></span>  
  
```  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {   
                DisplayName + " One",   
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a><span data-ttu-id="191d7-117">Hizmet yayımlama</span><span class="sxs-lookup"><span data-stu-id="191d7-117">Publishing a service</span></span>  
 <span data-ttu-id="191d7-118">Bir tasarımcı bir hizmeti kullanmak, önce kullanarak ana bilgisayar tarafından yayımlanmalıdır <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="191d7-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="191d7-119">Bir hizmete abone olma</span><span class="sxs-lookup"><span data-stu-id="191d7-119">Subscribing to a service</span></span>  
 <span data-ttu-id="191d7-120">Tasarımcı hizmetini kullanarak erişim elde <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> yönteminde <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="191d7-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="191d7-121">Aşağıdaki kod parçacığında, bir hizmete abone olmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="191d7-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;   
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="191d7-122">Öğe koleksiyonunun kullanarak veri paylaşımı</span><span class="sxs-lookup"><span data-stu-id="191d7-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="191d7-123">Öğe koleksiyonunun kullanarak Hizmetleri koleksiyonu hariç kullanmaya benzer <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> Yayımla yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="191d7-124">Bu koleksiyon tasarımcıları ve ana bilgisayar yerine karmaşık işlevleri arasında basit veri paylaşımı için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="191d7-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="191d7-125">EditingContext ana bilgisayar öğeleri ve Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="191d7-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="191d7-126">.Net Framework bir dizi yerleşik öğeleri ve düzenleme bağlam erişilen hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-126">The .Net Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="191d7-127">Öğeleri:</span><span class="sxs-lookup"><span data-stu-id="191d7-127">Items:</span></span>  
  
-   <span data-ttu-id="191d7-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: İş akışı içinde denetimleri (örneğin, ifade Düzenleyicisi) için kullanılan başvurulan yerel derleme listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="191d7-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
-   <span data-ttu-id="191d7-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcı bir salt okunur durumda olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="191d7-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
-   <span data-ttu-id="191d7-130"><xref:System.Activities.Presentation.View.Selection>: Şu anda seçili nesneler koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
-   <span data-ttu-id="191d7-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="191d7-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
-   <span data-ttu-id="191d7-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Şimdiki düzenleme oturumunda dayanır dosya hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="191d7-133">Hizmetler:</span><span class="sxs-lookup"><span data-stu-id="191d7-133">Services:</span></span>  
  
-   <span data-ttu-id="191d7-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Sağlar geçerli örneğine eklenecek özellikleri kullanarak <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="191d7-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
-   <span data-ttu-id="191d7-135"><xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvaline özelliklerine erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
-   <span data-ttu-id="191d7-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Güncelleştirilmesi için araç içeriği sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
-   <span data-ttu-id="191d7-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (örneğin, bağlam menüsü) sağlanan özel hizmet uygulamaları ile tümleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
-   <span data-ttu-id="191d7-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcı için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
-   <span data-ttu-id="191d7-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: İfade Düzenleyicisi iletişim erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
-   <span data-ttu-id="191d7-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcı ile tümleşik Yardım işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
-   <span data-ttu-id="191d7-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Kullanarak doğrulama hataları erişim sağlayan <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="191d7-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
-   <span data-ttu-id="191d7-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Depolamak ve veri almak için bir iç hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="191d7-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="191d7-143">Bu hizmet .net tarafından dahili olarak kullanılır, Framework ve dış kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="191d7-143">This service is used internally by the .Net Framework, and is not intended for external use.</span></span>  
  
-   <span data-ttu-id="191d7-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: XAML yük hata koleksiyonu kullanarak erişim sağlayan <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="191d7-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
-   <span data-ttu-id="191d7-145"><xref:System.Activities.Presentation.Services.ModelService>: İş akışı düzenlenmekte olan modeli ile etkileşim için tasarımcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
-   <span data-ttu-id="191d7-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Model öğesi ağaç kullanarak kök erişim sağlayan <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="191d7-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
-   <span data-ttu-id="191d7-147"><xref:System.Activities.Presentation.UndoEngine>: Geri alma sağlar ve işlevsellik yineleyin.</span><span class="sxs-lookup"><span data-stu-id="191d7-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
-   <span data-ttu-id="191d7-148"><xref:System.Activities.Presentation.Services.ViewService>: Görsel öğelerin temeldeki model öğelerine eşler.</span><span class="sxs-lookup"><span data-stu-id="191d7-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
-   <span data-ttu-id="191d7-149"><xref:System.Activities.Presentation.View.ViewStateService>: Depoları modeli öğeleri durumlarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="191d7-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
-   <span data-ttu-id="191d7-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı UI davranışını özelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
-   <span data-ttu-id="191d7-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Kaydetmek ve olay bildirimleri için temsilciler kaydını kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191d7-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="191d7-152">Ayrıca bir pencere sahibinin ayarlanması olanak verir.</span><span class="sxs-lookup"><span data-stu-id="191d7-152">Also allows a window owner to be set.</span></span>
