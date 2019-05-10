---
title: ModelItem Düzenleme Bağlamını Kullanma
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 8b2f2b8d4c528de14ea8b37e4eda8190f1757c22
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664699"
---
# <a name="using-the-modelitem-editing-context"></a>ModelItem Düzenleme Bağlamını Kullanma
<xref:System.Activities.Presentation.Model.ModelItem> İçerik düzenleme, tasarımcı ile iletişim kurmak için ana bilgisayar uygulaması kullanan nesnedir. <xref:System.Activities.Presentation.EditingContext> iki yöntem sunar <xref:System.Activities.Presentation.EditingContext.Items%2A> ve <xref:System.Activities.Presentation.EditingContext.Services%2A>, kullanılabilir  
  
## <a name="the-items-collection"></a>Öğeleri koleksiyonu  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Koleksiyon konak ve tasarımcı arasında paylaşılan veri veya tüm tasarımcıları için kullanılabilir olan verilerine erişmek için kullanılır. Üzerinden erişilen aşağıdaki özellikleri, bu koleksiyona sahip <xref:System.Activities.Presentation.ContextItemManager> sınıfı:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Hizmetler koleksiyonu  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Koleksiyon, tüm tasarımcıları kullanan hizmetler veya tasarımcı konak ile etkileşim kurmak için kullandığı hizmetler erişmek için kullanılır. Bu koleksiyon Not aşağıdaki yöntemleri vardır:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Bir etkinlik bir tasarımcı atama  
 Bir etkinlik kullanan hangi Tasarımcısı belirtmek için tasarımcı özniteliği kullanılır.  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>Hizmet oluşturma  
 Tasarımcı ile konak arasındaki bilgilerinin bir conduit görevi gören bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulması gerekir. Arabirim tarafından kullanılan <xref:System.Activities.Presentation.ServiceManager.Publish%2A> hizmet ve uygulama üyelerini tanımlamak için yöntem hizmeti için mantık içerir. Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.  
  
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
  
## <a name="publishing-a-service"></a>Bir hizmeti yayımlama  
 Bir hizmeti kullanmak için bir tasarımcı için bunu önce kullanarak ana bilgisayar tarafından yayımlanmalıdır <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi.  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Bir hizmete abone olma  
 Tasarımcı hizmetini kullanarak erişim elde eder <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> yönteminde <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemi. Aşağıdaki kod parçacığı bir hizmete abone gösterilmektedir.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Öğe koleksiyonunun kullanarak veri paylaşımı  
 Öğe koleksiyonunun kullanarak hariç hizmetler koleksiyonunun kullanmaya benzer <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> Yayımla yerine kullanılır. Bu koleksiyonu daha basit veri tasarımcıları ve konak yerine karmaşık işlevleri arasında paylaşmak için uygundur.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext konak öğelerine ve Hizmetleri  
 .NET Framework, bir dizi yerleşik öğeleri ve düzenleme bağlamı erişilen hizmetler sağlar.  
  
 Öğeler:  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: İş akışı içinde denetimler (örneğin, ifade düzenleyicisini) için kullanılan yerel başvurulan derlemelerin listesini yönetir.  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcı, bir salt okunur durumda olup olmadığını gösterir.  
  
- <xref:System.Activities.Presentation.View.Selection>: Şu anda seçili olan nesnelerinin koleksiyonunu tanımlar.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Geçerli düzenleme oturumunu temel alan bir dosya hakkında bilgi sağlar.  
  
 Hizmetler:  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Geçerli örneğine eklenecek özellikleri sağlayan kullanarak <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvaline özelliklerine erişim sağlar.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Güncelleştirilecek araç içeriğini sağlar.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (örneğin, bağlam menüsü) özel tarafından sağlanan hizmet uygulamaları ile tümleştirme için kullanılır.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcı için işlevsellik sağlar.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: İfade Düzenleyicisi iletişim erişim sağlar.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcı, tümleşik Yardım işlevleri sunar.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Doğrulama hataları kullanarak erişim sağlayan <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Veri depolayıp almak için bir iç hizmet sağlar. Bu hizmet, .NET Framework tarafından dahili olarak kullanılır ve dış kullanılmak üzere tasarlanmamıştır.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: XAML yükleme koleksiyonu kullanarak bir hata için erişim sağlayan <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: İş akışının düzenlenmekte olan modeli ile etkileşim için tasarımcı tarafından kullanılır.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Model öğesi ağacı kullanarak kök erişim sağlayan <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Geri alma sağlar ve işlevsellik Yinele.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Görsel öğeler, temel alınan model öğelerine eşler.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Model öğeleri için durumları depolarını görüntüleyin.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal bir kapsayıcı UI davranışını özelleştirmek için kullanılır.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Kaydolun ve olay bildirimleri için temsilcileri kaydını silmek için kullanılır. Bir pencere sahibi ayarlamak de sağlar.
