---
description: 'Hakkında daha fazla bilgi edinin: Modelıdıtem Editing bağlamını kullanma'
title: ModelItem Düzenleme Bağlamını Kullanma
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 7b6b9015f250d0e52f15e574f62386fa94a68e11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755024"
---
# <a name="using-the-modelitem-editing-context"></a>ModelItem Düzenleme Bağlamını Kullanma

<xref:System.Activities.Presentation.Model.ModelItem>Düzen bağlamı, ana bilgisayar uygulamasının tasarımcı ile iletişim kurmak için kullandığı nesnedir. <xref:System.Activities.Presentation.EditingContext> iki yöntem sunar <xref:System.Activities.Presentation.EditingContext.Items%2A> ve <xref:System.Activities.Presentation.EditingContext.Services%2A> Bu şekilde kullanılabilir  
  
## <a name="the-items-collection"></a>Öğeler koleksiyonu  

 <xref:System.Activities.Presentation.EditingContext.Items%2A>Koleksiyon, konak ve tasarımcı arasında paylaşılan verilere veya tüm tasarımcılar tarafından kullanılabilen verilere erişmek için kullanılır. Bu koleksiyon, sınıfı aracılığıyla erişilen aşağıdaki yeteneklere sahiptir <xref:System.Activities.Presentation.ContextItemManager> :  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Hizmetler koleksiyonu  

 <xref:System.Activities.Presentation.EditingContext.Services%2A>Koleksiyon, tasarımcının konak ile veya tüm tasarımcılarının kullandığı hizmetlerle etkileşim kurmak için kullandığı hizmetlere erişmek için kullanılır. Bu koleksiyonda aşağıdaki Note yöntemleri vardır:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Tasarımcı bir etkinlik atama  

 Bir etkinliğin hangi tasarımcı tarafından kullanıldığını belirtmek için tasarımcı özniteliği kullanılır.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Hizmet oluşturma  

 Tasarımcı ile konak arasında bilgi sunan bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulmalıdır. Arabirim, <xref:System.Activities.Presentation.ServiceManager.Publish%2A> hizmet üyelerini tanımlamak için yöntemi tarafından kullanılır ve uygulama hizmet mantığını içerir. Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.  
  
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
  
## <a name="publishing-a-service"></a>Hizmet yayımlama  

 Bir tasarımcının bir hizmeti tüketmesi için öncelikle yöntemi kullanılarak ana bilgisayar tarafından yayımlanması gerekir <xref:System.Activities.Presentation.ServiceManager.Publish%2A> .  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Bir hizmete abone olma  

 Tasarımcı, yöntemindeki yöntemi kullanarak hizmete erişim edinir <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> . Aşağıdaki kod parçacığı, bir hizmete nasıl abone olunacağını göstermektedir.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Öğeler koleksiyonunu kullanarak veri paylaşma  

 Öğeler koleksiyonunu kullanmak, yayınlama yerine kullanılması dışında, hizmetler koleksiyonunu kullanmakla benzerdir <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> . Bu koleksiyon, karmaşık bir işlevsellik yerine tasarımcılar ve ana bilgisayar arasında basit verileri paylaştırmak için daha uygundur.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext konak öğeleri ve Hizmetleri  

 .NET Framework, yapılandırma bağlamından erişilen bir dizi yerleşik öğe ve hizmeti sağlar.  
  
 Öğeler  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Denetimler için iş akışı içinde kullanılacak başvurulan yerel derlemelerin listesini yönetir (ifade Düzenleyicisi gibi).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcının salt okuma durumunda olup olmadığını gösterir.  
  
- <xref:System.Activities.Presentation.View.Selection>: Şu anda seçili olan nesnelerin koleksiyonunu tanımlar.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleyen oturumun temel aldığı dosya hakkında bilgi sağlar.  
  
 Hizmetler:  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Özellikleri, kullanılarak geçerli örneğe eklenmesine izin verir <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A> .  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvalinin özelliklerine erişime izin verir.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Araç kutusu içeriğinin güncelleştirilmesini sağlar.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Özel sağlanmış hizmet uygulamalarıyla tasarımcı komutlarını (bağlam menüsü gibi) bütünleştirmek için kullanılır.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcısı için işlevsellik sağlar.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Ifade Düzenleyicisi iletişim kutusuna erişim sağlar.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcıyı tümleşik yardım işlevleriyle sağlar.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Kullanılarak doğrulama hatalarına erişim sağlar <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> .  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Verileri depolamak ve almak için bir iç hizmet sağlar. Bu hizmet .NET Framework tarafından dahili olarak kullanılır ve dış kullanım için tasarlanmamıştır.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Kullanarak XAML yükleme hata koleksiyonuna erişim sağlar <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A> .  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Düzenlenmekte olan iş akışının modeliyle etkileşim kurmak için tasarımcı tarafından kullanılır.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Kullanarak model öğesi ağacının köküne erişim sağlar <xref:System.Activities.Presentation.Model.ModelItem.Root%2A> .  
  
- <xref:System.Activities.Presentation.UndoEngine>: Geri al ve Yinele işlevlerini sağlar.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeleri temeldeki model öğelerine eşler.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için görünüm durumlarını depolar.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı kullanıcı arabirimi davranışını özelleştirmek için kullanılır.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Olay bildirimleri için temsilcileri kaydettirmek ve kaydını silmek için kullanılır. Ayrıca bir pencere sahibinin ayarlanalmasına izin verir.
