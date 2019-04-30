---
title: ModelItem Düzenleme Bağlamını Kullanma
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a2628bbbf2f6684e5d484b05cd5a2ac622f3b664
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669504"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="82bbd-102">ModelItem Düzenleme Bağlamını Kullanma</span><span class="sxs-lookup"><span data-stu-id="82bbd-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="82bbd-103"><xref:System.Activities.Presentation.Model.ModelItem> İçerik düzenleme, tasarımcı ile iletişim kurmak için ana bilgisayar uygulaması kullanan nesnedir.</span><span class="sxs-lookup"><span data-stu-id="82bbd-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="82bbd-104"><xref:System.Activities.Presentation.EditingContext> iki yöntem sunar <xref:System.Activities.Presentation.EditingContext.Items%2A> ve <xref:System.Activities.Presentation.EditingContext.Services%2A>, kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="82bbd-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="82bbd-105">Öğeleri koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="82bbd-105">The Items collection</span></span>  
 <span data-ttu-id="82bbd-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Koleksiyon konak ve tasarımcı arasında paylaşılan veri veya tüm tasarımcıları için kullanılabilir olan verilerine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="82bbd-107">Üzerinden erişilen aşağıdaki özellikleri, bu koleksiyona sahip <xref:System.Activities.Presentation.ContextItemManager> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="82bbd-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="82bbd-108">Hizmetler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="82bbd-108">The Services collection</span></span>  
 <span data-ttu-id="82bbd-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Koleksiyon, tüm tasarımcıları kullanan hizmetler veya tasarımcı konak ile etkileşim kurmak için kullandığı hizmetler erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="82bbd-110">Bu koleksiyon Not aşağıdaki yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="82bbd-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="82bbd-111">Bir etkinlik bir tasarımcı atama</span><span class="sxs-lookup"><span data-stu-id="82bbd-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="82bbd-112">Bir etkinlik kullanan hangi Tasarımcısı belirtmek için tasarımcı özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="82bbd-113">Hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="82bbd-113">Creating a service</span></span>  
 <span data-ttu-id="82bbd-114">Tasarımcı ile konak arasındaki bilgilerinin bir conduit görevi gören bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82bbd-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="82bbd-115">Arabirim tarafından kullanılan <xref:System.Activities.Presentation.ServiceManager.Publish%2A> hizmet ve uygulama üyelerini tanımlamak için yöntem hizmeti için mantık içerir.</span><span class="sxs-lookup"><span data-stu-id="82bbd-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="82bbd-116">Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82bbd-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="82bbd-117">Bir hizmeti yayımlama</span><span class="sxs-lookup"><span data-stu-id="82bbd-117">Publishing a service</span></span>  
 <span data-ttu-id="82bbd-118">Bir hizmeti kullanmak için bir tasarımcı için bunu önce kullanarak ana bilgisayar tarafından yayımlanmalıdır <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="82bbd-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="82bbd-119">Bir hizmete abone olma</span><span class="sxs-lookup"><span data-stu-id="82bbd-119">Subscribing to a service</span></span>  
 <span data-ttu-id="82bbd-120">Tasarımcı hizmetini kullanarak erişim elde eder <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> yönteminde <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="82bbd-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="82bbd-121">Aşağıdaki kod parçacığı bir hizmete abone gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82bbd-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="82bbd-122">Öğe koleksiyonunun kullanarak veri paylaşımı</span><span class="sxs-lookup"><span data-stu-id="82bbd-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="82bbd-123">Öğe koleksiyonunun kullanarak hariç hizmetler koleksiyonunun kullanmaya benzer <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> Yayımla yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="82bbd-124">Bu koleksiyonu daha basit veri tasarımcıları ve konak yerine karmaşık işlevleri arasında paylaşmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="82bbd-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="82bbd-125">EditingContext konak öğelerine ve Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="82bbd-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="82bbd-126">.NET Framework, bir dizi yerleşik öğeleri ve düzenleme bağlamı erişilen hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="82bbd-127">Öğeler:</span><span class="sxs-lookup"><span data-stu-id="82bbd-127">Items:</span></span>  
  
- <span data-ttu-id="82bbd-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: İş akışı içinde denetimler (örneğin, ifade düzenleyicisini) için kullanılan yerel başvurulan derlemelerin listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="82bbd-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="82bbd-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcı, bir salt okunur durumda olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="82bbd-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="82bbd-130"><xref:System.Activities.Presentation.View.Selection>: Şu anda seçili olan nesnelerinin koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="82bbd-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="82bbd-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="82bbd-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleme oturumunu temel alan bir dosya hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="82bbd-133">Hizmetler:</span><span class="sxs-lookup"><span data-stu-id="82bbd-133">Services:</span></span>  
  
- <span data-ttu-id="82bbd-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Geçerli örneğine eklenecek özellikleri sağlayan kullanarak <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="82bbd-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="82bbd-135"><xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvaline özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="82bbd-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Güncelleştirilecek araç içeriğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="82bbd-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (örneğin, bağlam menüsü) özel tarafından sağlanan hizmet uygulamaları ile tümleştirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="82bbd-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcı için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="82bbd-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: İfade Düzenleyicisi iletişim erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="82bbd-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcı, tümleşik Yardım işlevleri sunar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="82bbd-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Doğrulama hataları kullanarak erişim sağlayan <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="82bbd-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="82bbd-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Veri depolayıp almak için bir iç hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="82bbd-143">Bu hizmet, .NET Framework tarafından dahili olarak kullanılır ve dış kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="82bbd-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: XAML yükleme koleksiyonu kullanarak bir hata için erişim sağlayan <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="82bbd-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="82bbd-145"><xref:System.Activities.Presentation.Services.ModelService>: İş akışının düzenlenmekte olan modeli ile etkileşim için tasarımcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="82bbd-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Model öğesi ağacı kullanarak kök erişim sağlayan <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="82bbd-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="82bbd-147"><xref:System.Activities.Presentation.UndoEngine>: Geri alma sağlar ve işlevsellik Yinele.</span><span class="sxs-lookup"><span data-stu-id="82bbd-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="82bbd-148"><xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeler, temel alınan model öğelerine eşler.</span><span class="sxs-lookup"><span data-stu-id="82bbd-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="82bbd-149"><xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için durumları depolarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="82bbd-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="82bbd-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal bir kapsayıcı UI davranışını özelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="82bbd-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Kaydolun ve olay bildirimleri için temsilcileri kaydını silmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bbd-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="82bbd-152">Bir pencere sahibi ayarlamak de sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bbd-152">Also allows a window owner to be set.</span></span>
