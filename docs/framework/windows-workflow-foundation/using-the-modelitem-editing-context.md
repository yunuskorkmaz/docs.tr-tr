---
title: ModelItem Düzenleme Bağlamını Kullanma
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: e1481d96e39f837d72834222d2839c520e880cc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142520"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="d6100-102">ModelItem Düzenleme Bağlamını Kullanma</span><span class="sxs-lookup"><span data-stu-id="d6100-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="d6100-103">Düzenleme <xref:System.Activities.Presentation.Model.ModelItem> bağlamı, ana bilgisayar uygulamasının tasarımcıyla iletişim kurmak için kullandığı nesnedir.</span><span class="sxs-lookup"><span data-stu-id="d6100-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="d6100-104"><xref:System.Activities.Presentation.EditingContext>iki yöntem ortaya <xref:System.Activities.Presentation.EditingContext.Items%2A> <xref:System.Activities.Presentation.EditingContext.Services%2A>çıkarır ve , hangi kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="d6100-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="d6100-105">Öğeler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="d6100-105">The Items collection</span></span>  
 <span data-ttu-id="d6100-106">Koleksiyon, <xref:System.Activities.Presentation.EditingContext.Items%2A> ana bilgisayar ile tasarımcı arasında paylaşılan verilere veya tüm tasarımcıların kullanabileceği verilere erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6100-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="d6100-107">Bu koleksiyon, <xref:System.Activities.Presentation.ContextItemManager> sınıf üzerinden erişilen aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d6100-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="d6100-108">Hizmetler koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="d6100-108">The Services collection</span></span>  
 <span data-ttu-id="d6100-109">Koleksiyon, <xref:System.Activities.Presentation.EditingContext.Services%2A> tasarımcının ana bilgisayarla etkileşimde kullanılmak üzere kullandığı hizmetlere veya tüm tasarımcıların kullandığı hizmetlere erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6100-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="d6100-110">Bu koleksiyonda aşağıdaki not yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="d6100-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="d6100-111">Tasarımcıya etkinlik atama</span><span class="sxs-lookup"><span data-stu-id="d6100-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="d6100-112">Bir etkinliğin hangi tasarımcıyı kullandığını belirtmek için Tasarımcı özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6100-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="d6100-113">Hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6100-113">Creating a service</span></span>  
 <span data-ttu-id="d6100-114">Tasarımcı ve ana bilgisayar arasında bilgi kanalı olarak hizmet veren bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6100-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="d6100-115">Arabirim, hizmetin <xref:System.Activities.Presentation.ServiceManager.Publish%2A> üyelerini tanımlamak için yöntem tarafından kullanılır ve uygulama hizmet için mantık içerir.</span><span class="sxs-lookup"><span data-stu-id="d6100-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="d6100-116">Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d6100-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="d6100-117">Hizmet yayımlama</span><span class="sxs-lookup"><span data-stu-id="d6100-117">Publishing a service</span></span>  
 <span data-ttu-id="d6100-118">Bir tasarımcının bir hizmeti tüketmesi için, önce <xref:System.Activities.Presentation.ServiceManager.Publish%2A> bu yöntem kullanılarak ana bilgisayar tarafından yayımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6100-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="d6100-119">Bir hizmete abone olma</span><span class="sxs-lookup"><span data-stu-id="d6100-119">Subscribing to a service</span></span>  
 <span data-ttu-id="d6100-120">Tasarımcı, <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemdeki yöntemi kullanarak hizmete erişim elde eder.</span><span class="sxs-lookup"><span data-stu-id="d6100-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="d6100-121">Aşağıdaki kod snippet nasıl bir hizmete abone olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6100-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="d6100-122">Öğeler koleksiyonunu kullanarak veri paylaşımı</span><span class="sxs-lookup"><span data-stu-id="d6100-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="d6100-123">Öğeler koleksiyonunu kullanmak, Yayımlama yerine kullanılanlar <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> dışında Hizmetler koleksiyonunu kullanmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="d6100-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="d6100-124">Bu koleksiyon, karmaşık işlevsellik yerine basit verileri tasarımcılar ve ana bilgisayar arasında paylaşmak için daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="d6100-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="d6100-125">DüzenlemeBağlam ana bilgisayar öğeleri ve hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d6100-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="d6100-126">.NET Framework, düzenleme bağlamında erişilen bir dizi yerleşik öğe ve hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="d6100-127">Bileşen:</span><span class="sxs-lookup"><span data-stu-id="d6100-127">Items:</span></span>  
  
- <span data-ttu-id="d6100-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Denetimler için iş akışı içinde kullanılacak başvurulan yerel derlemelerin listesini yönetir (ifade düzenleyicisi gibi).</span><span class="sxs-lookup"><span data-stu-id="d6100-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="d6100-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcının salt okunur durumda olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6100-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="d6100-130"><xref:System.Activities.Presentation.View.Selection>: Şu anda seçili nesnelerin toplanmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="d6100-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="d6100-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="d6100-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleme oturumunun dayandığı dosya hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="d6100-133">Hizmetler:</span><span class="sxs-lookup"><span data-stu-id="d6100-133">Services:</span></span>  
  
- <span data-ttu-id="d6100-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Özelliklerin geçerli örneğe eklenmesini sağlar, . <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A></span><span class="sxs-lookup"><span data-stu-id="d6100-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="d6100-135"><xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvalin özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="d6100-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Araç kutusunun içeriğinin güncellenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d6100-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="d6100-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (Bağlam Menüsü gibi) özel olarak sağlanan hizmet uygulamalarıyla tümleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6100-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="d6100-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklama için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="d6100-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: İfade Düzenleyicisi iletişim kutusuna erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="d6100-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcıya entegre yardım işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="d6100-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Doğrulama hatalarına erişim <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="d6100-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Verileri depolamak ve almak için dahili bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="d6100-143">Bu hizmet .NET Framework tarafından dahili olarak kullanılır ve harici kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="d6100-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="d6100-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: XAML yük hatası koleksiyonuna <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="d6100-145"><xref:System.Activities.Presentation.Services.ModelService>: Tasarımcı tarafından düzenlenen iş akışının modeliyle etkileşimde kullanılmak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6100-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="d6100-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Model öğesi ağacının köküne <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="d6100-147"><xref:System.Activities.Presentation.UndoEngine>: Geri ave ve yeniden yapma işlevselliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6100-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="d6100-148"><xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeleri temel model öğeleriyle eşler.</span><span class="sxs-lookup"><span data-stu-id="d6100-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="d6100-149"><xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için görünüm durumları depolar.</span><span class="sxs-lookup"><span data-stu-id="d6100-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="d6100-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı UI davranışını özelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6100-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="d6100-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Olay bildirimleri için temsilcileri kaydetmek ve kayıt dışı kullanmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6100-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="d6100-152">Ayrıca bir pencere sahibinin ayarlanmasına da izin verir.</span><span class="sxs-lookup"><span data-stu-id="d6100-152">Also allows a window owner to be set.</span></span>
