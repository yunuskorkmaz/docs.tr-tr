---
title: ModelItem Düzenleme Bağlamını Kullanma
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a47cb53e50d221c0ae07cf0841688fe4f8ced7d4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988917"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="77454-102">ModelItem Düzenleme Bağlamını Kullanma</span><span class="sxs-lookup"><span data-stu-id="77454-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="77454-103"><xref:System.Activities.Presentation.Model.ModelItem> Düzen bağlamı, ana bilgisayar uygulamasının tasarımcı ile iletişim kurmak için kullandığı nesnedir.</span><span class="sxs-lookup"><span data-stu-id="77454-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="77454-104"><xref:System.Activities.Presentation.EditingContext>iki yöntem <xref:System.Activities.Presentation.EditingContext.Items%2A> sunar ve <xref:System.Activities.Presentation.EditingContext.Services%2A>bu şekilde kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="77454-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="77454-105">Öğeler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="77454-105">The Items collection</span></span>  
 <span data-ttu-id="77454-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Koleksiyon, konak ve tasarımcı arasında paylaşılan verilere veya tüm tasarımcılar tarafından kullanılabilen verilere erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77454-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="77454-107">Bu koleksiyon, <xref:System.Activities.Presentation.ContextItemManager> sınıfı aracılığıyla erişilen aşağıdaki yeteneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="77454-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="77454-108">Hizmetler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="77454-108">The Services collection</span></span>  
 <span data-ttu-id="77454-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Koleksiyon, tasarımcının konak ile veya tüm tasarımcılarının kullandığı hizmetlerle etkileşim kurmak için kullandığı hizmetlere erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77454-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="77454-110">Bu koleksiyonda aşağıdaki Note yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="77454-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="77454-111">Tasarımcı bir etkinlik atama</span><span class="sxs-lookup"><span data-stu-id="77454-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="77454-112">Bir etkinliğin hangi tasarımcı tarafından kullanıldığını belirtmek için tasarımcı özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77454-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="77454-113">Hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="77454-113">Creating a service</span></span>  
 <span data-ttu-id="77454-114">Tasarımcı ile konak arasında bilgi sunan bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77454-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="77454-115">Arabirim, hizmet üyelerini tanımlamak için <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi tarafından kullanılır ve uygulama hizmet mantığını içerir.</span><span class="sxs-lookup"><span data-stu-id="77454-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="77454-116">Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="77454-116">In the following code example, a service interface and implementation are created.</span></span>  
  
```csharp  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="77454-117">Hizmet yayımlama</span><span class="sxs-lookup"><span data-stu-id="77454-117">Publishing a service</span></span>  
 <span data-ttu-id="77454-118">Bir tasarımcının bir hizmeti tüketmesi için öncelikle <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi kullanılarak ana bilgisayar tarafından yayımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77454-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="77454-119">Bir hizmete abone olma</span><span class="sxs-lookup"><span data-stu-id="77454-119">Subscribing to a service</span></span>  
 <span data-ttu-id="77454-120">Tasarımcı, <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemindeki yöntemi kullanarak hizmete erişim edinir.</span><span class="sxs-lookup"><span data-stu-id="77454-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="77454-121">Aşağıdaki kod parçacığı, bir hizmete nasıl abone olunacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="77454-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```csharp  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="77454-122">Öğeler koleksiyonunu kullanarak veri paylaşma</span><span class="sxs-lookup"><span data-stu-id="77454-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="77454-123">Öğeler koleksiyonunu kullanmak, yayınlama yerine kullanılması dışında <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> , hizmetler koleksiyonunu kullanmakla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="77454-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="77454-124">Bu koleksiyon, karmaşık bir işlevsellik yerine tasarımcılar ve ana bilgisayar arasında basit verileri paylaştırmak için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="77454-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="77454-125">EditingContext konak öğeleri ve Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="77454-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="77454-126">.NET Framework, yapılandırma bağlamından erişilen bir dizi yerleşik öğe ve hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="77454-127">Öğeler</span><span class="sxs-lookup"><span data-stu-id="77454-127">Items:</span></span>  
  
- <span data-ttu-id="77454-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: , Denetimler için iş akışında kullanılacak Başvurulmuş yerel derlemelerin listesini yönetir (ifade Düzenleyicisi gibi).</span><span class="sxs-lookup"><span data-stu-id="77454-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="77454-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcının salt okuma durumunda olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77454-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="77454-130"><xref:System.Activities.Presentation.View.Selection>: Şu anda seçili olan nesnelerin koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77454-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="77454-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="77454-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="77454-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleyen oturumun temel aldığı dosya hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="77454-133">Servislere</span><span class="sxs-lookup"><span data-stu-id="77454-133">Services:</span></span>  
  
- <span data-ttu-id="77454-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Özelliklerinin, kullanılarak <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>geçerli örneğe eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="77454-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="77454-135"><xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvalinin özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="77454-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Araç kutusu içeriğinin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="77454-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (bağlam menüsü gibi) özel olarak sağlanmış hizmet uygulamalarıyla bütünleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77454-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="77454-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcısı için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="77454-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Ifade Düzenleyicisi iletişim kutusuna erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="77454-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcı ile tümleşik yardım işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="77454-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Kullanılarak <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>doğrulama hatalarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="77454-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Verileri depolamak ve almak için bir iç hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="77454-143">Bu hizmet .NET Framework tarafından dahili olarak kullanılır ve dış kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="77454-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="77454-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Kullanılarak <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>XAML yükleme hatası koleksiyonuna erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="77454-145"><xref:System.Activities.Presentation.Services.ModelService>: Tasarımcı tarafından düzenlenmekte olan iş akışının modeliyle etkileşim kurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77454-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="77454-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Kullanılarak <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>model öğesi ağacının köküne erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="77454-147"><xref:System.Activities.Presentation.UndoEngine>: Geri al ve Yinele işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="77454-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="77454-148"><xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeleri temel model öğelerine eşler.</span><span class="sxs-lookup"><span data-stu-id="77454-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="77454-149"><xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için görünüm durumlarını depolar.</span><span class="sxs-lookup"><span data-stu-id="77454-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="77454-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı kullanıcı arabirimi davranışını özelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77454-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="77454-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Olay bildirimleri için temsilcileri kaydetmek ve kaydını silmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77454-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="77454-152">Ayrıca bir pencere sahibinin ayarlanalmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="77454-152">Also allows a window owner to be set.</span></span>
