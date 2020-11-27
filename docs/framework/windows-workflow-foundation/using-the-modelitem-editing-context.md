---
title: ModelItem Düzenleme Bağlamını Kullanma
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 2ab002f902833d3b1a69ea0b03b5ca589f4492d1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275976"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="6d45a-102">ModelItem Düzenleme Bağlamını Kullanma</span><span class="sxs-lookup"><span data-stu-id="6d45a-102">Using the ModelItem Editing Context</span></span>

<span data-ttu-id="6d45a-103"><xref:System.Activities.Presentation.Model.ModelItem>Düzen bağlamı, ana bilgisayar uygulamasının tasarımcı ile iletişim kurmak için kullandığı nesnedir.</span><span class="sxs-lookup"><span data-stu-id="6d45a-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="6d45a-104"><xref:System.Activities.Presentation.EditingContext> iki yöntem sunar <xref:System.Activities.Presentation.EditingContext.Items%2A> ve <xref:System.Activities.Presentation.EditingContext.Services%2A> Bu şekilde kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="6d45a-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="6d45a-105">Öğeler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="6d45a-105">The Items collection</span></span>  

 <span data-ttu-id="6d45a-106"><xref:System.Activities.Presentation.EditingContext.Items%2A>Koleksiyon, konak ve tasarımcı arasında paylaşılan verilere veya tüm tasarımcılar tarafından kullanılabilen verilere erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="6d45a-107">Bu koleksiyon, sınıfı aracılığıyla erişilen aşağıdaki yeteneklere sahiptir <xref:System.Activities.Presentation.ContextItemManager> :</span><span class="sxs-lookup"><span data-stu-id="6d45a-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="6d45a-108">Hizmetler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="6d45a-108">The Services collection</span></span>  

 <span data-ttu-id="6d45a-109"><xref:System.Activities.Presentation.EditingContext.Services%2A>Koleksiyon, tasarımcının konak ile veya tüm tasarımcılarının kullandığı hizmetlerle etkileşim kurmak için kullandığı hizmetlere erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="6d45a-110">Bu koleksiyonda aşağıdaki Note yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="6d45a-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="6d45a-111">Tasarımcı bir etkinlik atama</span><span class="sxs-lookup"><span data-stu-id="6d45a-111">Assigning a designer an activity</span></span>  

 <span data-ttu-id="6d45a-112">Bir etkinliğin hangi tasarımcı tarafından kullanıldığını belirtmek için tasarımcı özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="6d45a-113">Hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d45a-113">Creating a service</span></span>  

 <span data-ttu-id="6d45a-114">Tasarımcı ile konak arasında bilgi sunan bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="6d45a-115">Arabirim, <xref:System.Activities.Presentation.ServiceManager.Publish%2A> hizmet üyelerini tanımlamak için yöntemi tarafından kullanılır ve uygulama hizmet mantığını içerir.</span><span class="sxs-lookup"><span data-stu-id="6d45a-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="6d45a-116">Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6d45a-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="6d45a-117">Hizmet yayımlama</span><span class="sxs-lookup"><span data-stu-id="6d45a-117">Publishing a service</span></span>  

 <span data-ttu-id="6d45a-118">Bir tasarımcının bir hizmeti tüketmesi için öncelikle yöntemi kullanılarak ana bilgisayar tarafından yayımlanması gerekir <xref:System.Activities.Presentation.ServiceManager.Publish%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d45a-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="6d45a-119">Bir hizmete abone olma</span><span class="sxs-lookup"><span data-stu-id="6d45a-119">Subscribing to a service</span></span>  

 <span data-ttu-id="6d45a-120">Tasarımcı, yöntemindeki yöntemi kullanarak hizmete erişim edinir <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d45a-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="6d45a-121">Aşağıdaki kod parçacığı, bir hizmete nasıl abone olunacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6d45a-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="6d45a-122">Öğeler koleksiyonunu kullanarak veri paylaşma</span><span class="sxs-lookup"><span data-stu-id="6d45a-122">Sharing data using the Items collection</span></span>  

 <span data-ttu-id="6d45a-123">Öğeler koleksiyonunu kullanmak, yayınlama yerine kullanılması dışında, hizmetler koleksiyonunu kullanmakla benzerdir <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d45a-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="6d45a-124">Bu koleksiyon, karmaşık bir işlevsellik yerine tasarımcılar ve ana bilgisayar arasında basit verileri paylaştırmak için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="6d45a-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="6d45a-125">EditingContext konak öğeleri ve Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6d45a-125">EditingContext host items and services</span></span>  

 <span data-ttu-id="6d45a-126">.NET Framework, yapılandırma bağlamından erişilen bir dizi yerleşik öğe ve hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="6d45a-127">Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d45a-127">Items:</span></span>  
  
- <span data-ttu-id="6d45a-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Denetimler için iş akışı içinde kullanılacak başvurulan yerel derlemelerin listesini yönetir (ifade Düzenleyicisi gibi).</span><span class="sxs-lookup"><span data-stu-id="6d45a-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="6d45a-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcının salt okuma durumunda olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d45a-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="6d45a-130"><xref:System.Activities.Presentation.View.Selection>: Şu anda seçili olan nesnelerin koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="6d45a-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="6d45a-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="6d45a-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleyen oturumun temel aldığı dosya hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="6d45a-133">Hizmetler:</span><span class="sxs-lookup"><span data-stu-id="6d45a-133">Services:</span></span>  
  
- <span data-ttu-id="6d45a-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Özellikleri, kullanılarak geçerli örneğe eklenmesine izin verir <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d45a-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="6d45a-135"><xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvalinin özelliklerine erişime izin verir.</span><span class="sxs-lookup"><span data-stu-id="6d45a-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="6d45a-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Araç kutusu içeriğinin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="6d45a-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Özel sağlanmış hizmet uygulamalarıyla tasarımcı komutlarını (bağlam menüsü gibi) bütünleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="6d45a-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcısı için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="6d45a-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Ifade Düzenleyicisi iletişim kutusuna erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="6d45a-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcıyı tümleşik yardım işlevleriyle sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="6d45a-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Kullanılarak doğrulama hatalarına erişim sağlar <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d45a-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="6d45a-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Verileri depolamak ve almak için bir iç hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="6d45a-143">Bu hizmet .NET Framework tarafından dahili olarak kullanılır ve dış kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="6d45a-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Kullanarak XAML yükleme hata koleksiyonuna erişim sağlar <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d45a-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="6d45a-145"><xref:System.Activities.Presentation.Services.ModelService>: Düzenlenmekte olan iş akışının modeliyle etkileşim kurmak için tasarımcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="6d45a-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Kullanarak model öğesi ağacının köküne erişim sağlar <xref:System.Activities.Presentation.Model.ModelItem.Root%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d45a-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="6d45a-147"><xref:System.Activities.Presentation.UndoEngine>: Geri al ve Yinele işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="6d45a-148"><xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeleri temeldeki model öğelerine eşler.</span><span class="sxs-lookup"><span data-stu-id="6d45a-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="6d45a-149"><xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için görünüm durumlarını depolar.</span><span class="sxs-lookup"><span data-stu-id="6d45a-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="6d45a-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı kullanıcı arabirimi davranışını özelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="6d45a-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Olay bildirimleri için temsilcileri kaydettirmek ve kaydını silmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d45a-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="6d45a-152">Ayrıca bir pencere sahibinin ayarlanalmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6d45a-152">Also allows a window owner to be set.</span></span>
