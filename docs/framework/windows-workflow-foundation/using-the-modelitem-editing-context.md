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
# <a name="using-the-modelitem-editing-context"></a>Bağlam düzenleme ModelItem kullanma
<xref:System.Activities.Presentation.Model.ModelItem> Bağlam düzenleme nesnedir, konak uygulama Tasarımcısı ile iletişim kurmak için kullanır. <xref:System.Activities.Presentation.EditingContext>iki yöntem sunar <xref:System.Activities.Presentation.EditingContext.Items%2A> ve <xref:System.Activities.Presentation.EditingContext.Services%2A>, kullanılabilir  
  
## <a name="the-items-collection"></a>Öğeleri koleksiyonu  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Koleksiyonu Tasarımcısı ve ana bilgisayar arasında paylaşılan veri veya tüm tasarımcıları için kullanılabilir veri erişimi için kullanılır. Bu koleksiyon üzerinden erişilen aşağıdaki özellikleri içerir <xref:System.Activities.Presentation.ContextItemManager> sınıfı:  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Hizmetler koleksiyonu  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Koleksiyonu Tasarımcı konak ile etkileşim kurmak için kullandığı hizmetleri veya tüm tasarımcıları hizmetine erişmek için kullanılır. Bu koleksiyon Not aşağıdaki yöntemleri vardır:  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Bir etkinlik bir tasarımcı atama  
 Bir etkinliği kullanan hangi Tasarımcısı belirtmek için tasarımcı özniteliği kullanılır.  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>Bir hizmet oluşturma  
 Tasarımcı ve ana bilgisayar arasındaki bilgi conduit görevi gören bir hizmet oluşturmak için bir arabirim ve bir uygulama oluşturulması gerekir. Arabirim tarafından kullanılan <xref:System.Activities.Presentation.ServiceManager.Publish%2A> hizmet ve uygulama üyelerini tanımlamak üzere yöntemi hizmeti için mantık içerir. Aşağıdaki kod örneğinde, bir hizmet arabirimi ve uygulama oluşturulur.  
  
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
  
## <a name="publishing-a-service"></a>Hizmet yayımlama  
 Bir tasarımcı bir hizmeti kullanmak, önce kullanarak ana bilgisayar tarafından yayımlanmalıdır <xref:System.Activities.Presentation.ServiceManager.Publish%2A> yöntemi.  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Bir hizmete abone olma  
 Tasarımcı hizmetini kullanarak erişim elde <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> yönteminde <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> yöntemi. Aşağıdaki kod parçacığında, bir hizmete abone olmak gösterilmiştir.  
  
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
 Öğe koleksiyonunun kullanarak Hizmetleri koleksiyonu hariç kullanmaya benzer <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> Yayımla yerine kullanılır. Bu koleksiyon tasarımcıları ve ana bilgisayar yerine karmaşık işlevleri arasında basit veri paylaşımı için daha uygundur.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext ana bilgisayar öğeleri ve Hizmetleri  
 .Net Framework bir dizi yerleşik öğeleri ve düzenleme bağlam erişilen hizmetler sağlar.  
  
 Öğeleri:  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: İş akışı içinde denetimleri (örneğin, ifade Düzenleyicisi) için kullanılan başvurulan yerel derleme listesini yönetir.  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Tasarımcı bir salt okunur durumda olup olmadığını gösterir.  
  
-   <xref:System.Activities.Presentation.View.Selection>: Şu anda seçili nesneler koleksiyonunu tanımlar.  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem>: Şimdiki düzenleme oturumunda dayanır dosya hakkında bilgiler sağlar.  
  
 Hizmetler:  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Sağlar geçerli örneğine eklenecek özellikleri kullanarak <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
-   <xref:System.Activities.Presentation.View.DesignerView>: Tasarımcı tuvaline özelliklerine erişimi sağlar.  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService>: Güncelleştirilmesi için araç içeriği sağlar.  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService>: Tasarımcı komutlarını (örneğin, bağlam menüsü) sağlanan özel hizmet uygulamaları ile tümleştirmek için kullanılır.  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Tasarımcı hata ayıklayıcı için işlevsellik sağlar.  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService>: İfade Düzenleyicisi iletişim erişim sağlar.  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService>: Tasarımcı ile tümleşik Yardım işlevsellik sağlar.  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Kullanarak doğrulama hataları erişim sağlayan <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Depolamak ve veri almak için bir iç hizmet sağlar. Bu hizmet .net tarafından dahili olarak kullanılır, Framework ve dış kullanılmak üzere tasarlanmamıştır.  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService>: XAML yük hata koleksiyonu kullanarak erişim sağlayan <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
-   <xref:System.Activities.Presentation.Services.ModelService>: İş akışı düzenlenmekte olan modeli ile etkileşim için tasarımcı tarafından kullanılır.  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager>: Model öğesi ağaç kullanarak kök erişim sağlayan <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
-   <xref:System.Activities.Presentation.UndoEngine>: Geri alma sağlar ve işlevsellik yineleyin.  
  
-   <xref:System.Activities.Presentation.Services.ViewService>: Görsel öğelerin temeldeki model öğelerine eşler.  
  
-   <xref:System.Activities.Presentation.View.ViewStateService>: Depoları modeli öğeleri durumlarını görüntüleyin.  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Sanal kapsayıcı UI davranışını özelleştirmek için kullanılır.  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Kaydetmek ve olay bildirimleri için temsilciler kaydını kaldırmak için kullanılır. Ayrıca bir pencere sahibinin ayarlanması olanak verir.
