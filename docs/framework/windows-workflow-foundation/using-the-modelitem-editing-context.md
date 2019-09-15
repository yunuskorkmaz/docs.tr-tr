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
# <a name="using-the-modelitem-editing-context"></a>ModelItem Düzenleme Bağlamını Kullanma
<xref:System.Activities.Presentation.Model.ModelItem> Düzen bağlamı, ana bilgisayar uygulamasının tasarımcı ile iletişim kurmak için kullandığı nesnedir. <xref:System.Activities.Presentation.EditingContext>iki yöntem <xref:System.Activities.Presentation.EditingContext.Items%2A> sunar ve <xref:System.Activities.Presentation.EditingContext.Services%2A>bu şekilde kullanılabilir  
  
## <a name="the-items-collection"></a>Öğeler koleksiyonu  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Koleksiyon, konak ve tasarımcı arasında paylaşılan verilere veya tüm tasarımcılar tarafından kullanılabilen verilere erişmek için kullanılır. Bu koleksiyon, <xref:System.Activities.Presentation.ContextItemManager> sınıfı aracılığıyla erişilen aşağıdaki yeteneklere sahiptir:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Hizmetler koleksiyonu  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Koleksiyon, tasarımcının konak ile veya tüm tasarımcılarının kullandığı hizmetlerle etkileşim kurmak için kullandığı hizmetlere erişmek için kullanılır. Bu koleksiyonda aşağıdaki Note yöntemleri vardır:  
  
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
 Tasarımcı ile konak arasında bilgi sunan bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulmalıdır. Arabirim, hizmet üyelerini tanımlamak için <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi tarafından kullanılır ve uygulama hizmet mantığını içerir. Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.  
  
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
 Bir tasarımcının bir hizmeti tüketmesi için öncelikle <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi kullanılarak ana bilgisayar tarafından yayımlanması gerekir.  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Bir hizmete abone olma  
 Tasarımcı, <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemindeki yöntemi kullanarak hizmete erişim edinir. Aşağıdaki kod parçacığı, bir hizmete nasıl abone olunacağını göstermektedir.  
  
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
 Öğeler koleksiyonunu kullanmak, yayınlama yerine kullanılması dışında <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> , hizmetler koleksiyonunu kullanmakla benzerdir. Bu koleksiyon, karmaşık bir işlevsellik yerine tasarımcılar ve ana bilgisayar arasında basit verileri paylaştırmak için daha uygundur.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext konak öğeleri ve Hizmetleri  
 .NET Framework, yapılandırma bağlamından erişilen bir dizi yerleşik öğe ve hizmeti sağlar.  
  
 Öğeler  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: , Denetimler için iş akışında kullanılacak Başvurulmuş yerel derlemelerin listesini yönetir (ifade Düzenleyicisi gibi).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcının salt okuma durumunda olup olmadığını gösterir.  
  
- <xref:System.Activities.Presentation.View.Selection>: Şu anda seçili olan nesnelerin koleksiyonunu tanımlar.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleyen oturumun temel aldığı dosya hakkında bilgi sağlar.  
  
 Servislere  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Özelliklerinin, kullanılarak <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>geçerli örneğe eklenmesine izin verir.  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvalinin özelliklerine erişim sağlar.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Araç kutusu içeriğinin güncelleştirilmesini sağlar.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (bağlam menüsü gibi) özel olarak sağlanmış hizmet uygulamalarıyla bütünleştirmek için kullanılır.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcısı için işlevsellik sağlar.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Ifade Düzenleyicisi iletişim kutusuna erişim sağlar.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcı ile tümleşik yardım işlevlerini sağlar.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Kullanılarak <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>doğrulama hatalarına erişim sağlar.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Verileri depolamak ve almak için bir iç hizmet sağlar. Bu hizmet .NET Framework tarafından dahili olarak kullanılır ve dış kullanım için tasarlanmamıştır.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Kullanılarak <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>XAML yükleme hatası koleksiyonuna erişim sağlar.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Tasarımcı tarafından düzenlenmekte olan iş akışının modeliyle etkileşim kurmak için kullanılır.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Kullanılarak <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>model öğesi ağacının köküne erişim sağlar.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Geri al ve Yinele işlevlerini sağlar.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeleri temel model öğelerine eşler.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için görünüm durumlarını depolar.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı kullanıcı arabirimi davranışını özelleştirmek için kullanılır.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Olay bildirimleri için temsilcileri kaydetmek ve kaydını silmek için kullanılır. Ayrıca bir pencere sahibinin ayarlanalmasına izin verir.
