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
# <a name="using-the-modelitem-editing-context"></a>ModelItem Düzenleme Bağlamını Kullanma
Düzenleme <xref:System.Activities.Presentation.Model.ModelItem> bağlamı, ana bilgisayar uygulamasının tasarımcıyla iletişim kurmak için kullandığı nesnedir. <xref:System.Activities.Presentation.EditingContext>iki yöntem ortaya <xref:System.Activities.Presentation.EditingContext.Items%2A> <xref:System.Activities.Presentation.EditingContext.Services%2A>çıkarır ve , hangi kullanılabilir  
  
## <a name="the-items-collection"></a>Öğeler koleksiyonu  
 Koleksiyon, <xref:System.Activities.Presentation.EditingContext.Items%2A> ana bilgisayar ile tasarımcı arasında paylaşılan verilere veya tüm tasarımcıların kullanabileceği verilere erişmek için kullanılır. Bu koleksiyon, <xref:System.Activities.Presentation.ContextItemManager> sınıf üzerinden erişilen aşağıdaki özelliklere sahiptir:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Hizmetler koleksiyonu  
 Koleksiyon, <xref:System.Activities.Presentation.EditingContext.Services%2A> tasarımcının ana bilgisayarla etkileşimde kullanılmak üzere kullandığı hizmetlere veya tüm tasarımcıların kullandığı hizmetlere erişmek için kullanılır. Bu koleksiyonda aşağıdaki not yöntemleri vardır:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Tasarımcıya etkinlik atama  
 Bir etkinliğin hangi tasarımcıyı kullandığını belirtmek için Tasarımcı özniteliği kullanılır.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Hizmet oluşturma  
 Tasarımcı ve ana bilgisayar arasında bilgi kanalı olarak hizmet veren bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulmalıdır. Arabirim, hizmetin <xref:System.Activities.Presentation.ServiceManager.Publish%2A> üyelerini tanımlamak için yöntem tarafından kullanılır ve uygulama hizmet için mantık içerir. Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.  
  
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
 Bir tasarımcının bir hizmeti tüketmesi için, önce <xref:System.Activities.Presentation.ServiceManager.Publish%2A> bu yöntem kullanılarak ana bilgisayar tarafından yayımlanmalıdır.  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Bir hizmete abone olma  
 Tasarımcı, <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemdeki yöntemi kullanarak hizmete erişim elde eder. Aşağıdaki kod snippet nasıl bir hizmete abone olduğunu gösterir.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Öğeler koleksiyonunu kullanarak veri paylaşımı  
 Öğeler koleksiyonunu kullanmak, Yayımlama yerine kullanılanlar <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> dışında Hizmetler koleksiyonunu kullanmaya benzer. Bu koleksiyon, karmaşık işlevsellik yerine basit verileri tasarımcılar ve ana bilgisayar arasında paylaşmak için daha uygundur.  
  
## <a name="editingcontext-host-items-and-services"></a>DüzenlemeBağlam ana bilgisayar öğeleri ve hizmetleri  
 .NET Framework, düzenleme bağlamında erişilen bir dizi yerleşik öğe ve hizmet sağlar.  
  
 Bileşen:  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Denetimler için iş akışı içinde kullanılacak başvurulan yerel derlemelerin listesini yönetir (ifade düzenleyicisi gibi).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcının salt okunur durumda olup olmadığını gösterir.  
  
- <xref:System.Activities.Presentation.View.Selection>: Şu anda seçili nesnelerin toplanmasını tanımlar.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleme oturumunun dayandığı dosya hakkında bilgi sağlar.  
  
 Hizmetler:  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Özelliklerin geçerli örneğe eklenmesini sağlar, . <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvalin özelliklerine erişim sağlar.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Araç kutusunun içeriğinin güncellenmesine izin verir.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (Bağlam Menüsü gibi) özel olarak sağlanan hizmet uygulamalarıyla tümleştirmek için kullanılır.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklama için işlevsellik sağlar.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: İfade Düzenleyicisi iletişim kutusuna erişim sağlar.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcıya entegre yardım işlevselliği sağlar.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Doğrulama hatalarına erişim <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>sağlar.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Verileri depolamak ve almak için dahili bir hizmet sağlar. Bu hizmet .NET Framework tarafından dahili olarak kullanılır ve harici kullanım için tasarlanmamıştır.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: XAML yük hatası koleksiyonuna <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>erişim sağlar.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Tasarımcı tarafından düzenlenen iş akışının modeliyle etkileşimde kullanılmak üzere kullanılır.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Model öğesi ağacının köküne <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>erişim sağlar.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Geri ave ve yeniden yapma işlevselliğini sağlar.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeleri temel model öğeleriyle eşler.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için görünüm durumları depolar.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı UI davranışını özelleştirmek için kullanılır.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Olay bildirimleri için temsilcileri kaydetmek ve kayıt dışı kullanmak için kullanılır. Ayrıca bir pencere sahibinin ayarlanmasına da izin verir.
