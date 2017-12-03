---
title: "Nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362562c-767d-401b-8257-916616568fd4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0abc1ac1cea6c9799c3d6bb349869b77f1d0b7c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a>Nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma
İş akışı hizmetleri iş akışları IIS altında barındırılan / OLUŞTU. Başkası tarafından yazılmış bir iş akışı barındırma gerektiğinde kullanışlıdır. Örneğin, iş akışı Tasarımcısı'nı yeniden barındırma ve kullanıcılar kendi iş akışları oluşturmak izin verirseniz.  IIS'de hizmet olmayan iş akışı barındırma işlem geri dönüştürme, boşta kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme gibi özellikleri için destek sağlar. IIS barındırılan iş akışı hizmetleri içeren <xref:System.ServiceModel.Activities.Receive> etkinlikleri ve bu IIS tarafından bir ileti alındığında etkinleştirildi. Hizmet olmayan iş akışları Mesajlaşma etkinlikleri içermez ve bir ileti göndererek varsayılan olarak devre dışı bırakılamaz.  Öğesinden bir sınıf türetin <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ve iş akışı örneği oluşturmak için işlemleri içeren bir hizmet sözleşmesini tanımlama. Bu konu basit bir iş akışı oluşturma, bir istemci, iş akışını etkinleştirmek için kullanabileceğiniz bir hizmet sözleşmesini tanımlama ve öğesinden bir sınıf türetme size yol gösterecektir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> istekleri oluşturma iş akışı için dinlemek için hizmet sözleşmesi kullanır.  
  
### <a name="create-a-simple-workflow"></a>Basit bir iş akışı oluşturma  
  
1.  Yeni bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] boş adlı çözüm `CreationEndpointTest`.  
  
2.  Adlı yeni bir WCF iş akışı hizmeti uygulaması projesi eklemek `SimpleWorkflow` çözüme. İş Akışı Tasarımcısı'nı açar.  
  
3.  ReceiveRequest ve SendResponse etkinlikleri silin. Bu etkinlikler, bir iş akışını bir iş akışı hizmeti kılan ' dir. Bir iş akışı hizmeti ile çalışmayan olduğundan, artık bunları ihtiyacımız var.  
  
4.  DisplayName dizisi etkinliği için "Sıralı iş akışı" olarak ayarlayın.  
  
5.  Service1.xamlx Workflow1.xamlx için yeniden adlandırın.  
  
6.  Sıralı etkinlik dışında Tasarımcısı'nı tıklatın ve "Workflow1" için ad ve ConfigurationName özelliklerini ayarlama  
  
7.  Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence>. <xref:System.Activities.Statements.WriteLine> Etkinlik bulunabilir **Temelleri** araç bölümü. Ayarlama <xref:System.Activities.Statements.WriteLine.Text%2A> özelliği <xref:System.Activities.Statements.WriteLine> etkinliğe "Hello, world".  
  
     İş akışı, aşağıdaki diyagramda gibi görünmelidir.  
  
     ![Basit bir iş akışı](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")  
  
### <a name="create-the-workflow-creation-service-contract"></a>İş akışı oluşturma hizmet sözleşmesi oluşturma  
  
1.  Adlı yeni bir sınıf kitaplığı proje ekleme `Shared` için `CreationEndpointTest` çözümü.  
  
2.  System.ServiceModel.dll, System.Configuration ve System.ServiceModel.Activities için bir başvuru ekleyin `Shared` projesi.  
  
3.  Class1.cs dosyası IWorkflowCreation.cs ve aşağıdaki kodu dosyayı yeniden adlandırın.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     Bu sözleşme, iki işlem hem de yeni oluşturduğunuz hizmet olmayan iş akışı yeni bir örneğini oluşturmak tanımlar. Bir oluşturulan örnek Kimliğine sahip yeni bir örneğini oluşturur ve diğer yeni iş akışı örneği için örnek kimliği belirtmenize olanak tanır.  Her iki yöntem, yeni iş akışı örneği parametreler olanak tanır. Bu sözleşme tarafından sunulan <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> istemcilerin yeni bir hizmet olmayan iş akışı örneği oluşturmak izin vermek için.  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a>WorkflowHostingEndpoint bir sınıf türetin  
  
1.  Adlı yeni bir sınıf ekleyin `CreationEndpoint` türetilen <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> için `Shared` projesi.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  Yerel statik eklemek <xref:System.Uri> adlı değişken `defaultBaseUri` için `CreationEndpoint` sınıfı.  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  Aşağıdaki oluşturucuyu ekleyin `CreationEndpoint` sınıfı. Belirttiğimiz fark `IWorkflowCreation` temel oluşturucuyu çağrısında hizmet sözleşme.  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  Aşağıdaki varsayılan oluşturucu ekleyin `CreationEndpoint` sınıfı.  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  Statik eklemek `DefaultBaseUri` özelliğine `CreationEndpoint` sınıfı. Bu özellik, bir taban URI sağlanmamış varsayılan tutmak için kullanılır.  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  Oluşturma uç noktası için kullanılacak varsayılan bağlama almak için aşağıdaki yöntemi oluşturun.  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> iş akışı örneği kimliğine döndürülecek yöntemi Varsa `Action` "Oluştur" başlığı biter, boş bir GUID dönmek `Action` üstbilgi bitip GUID yönteme geçirilen "CreateWithInstanceId" return ile. Aksi takdirde, throw bir <xref:System.InvalidOperationException>. Bunlar `Action` üstbilgileri karşılık tanımlanan iki işlem `IWorkflowCreation` hizmet sözleşme.  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> yöntemi oluşturmak için bir <xref:System.ServiceModel.Activities.WorkflowCreationContext> ve iş akışı için herhangi bir bağımsız değişkeni ekleyin, örnek kimliği istemciye göndermek ve sonra geri dönüp <xref:System.ServiceModel.Activities.WorkflowCreationContext>.  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a>WorkflowCreationEndpoint yapılandırmanıza izin vermek için bir standart endpoint öğesi oluşturma  
  
1.  İçinde paylaşılan bir başvuru ekleyin `CreationEndpoint` proje  
  
2.  Adlı yeni bir sınıf ekleyin `CreationEndpointElement`, türetilmiş <xref:System.ServiceModel.Configuration.StandardEndpointElement> için `CreationEndpoint` projesi. Bu sınıfın temsil edecek bir `CreationEndpoint` web.config dosyasında.  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  Adlı bir özellik eklemek `EndpointType` uç nokta türünü dönün.  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  Geçersiz kılma <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> yöntemi ve yeni bir iade `CreationEndpoint`.  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  Aşırı yükleme <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, ve <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> yöntemleri. Bu yöntemler tanımlanmış olması yeterlidir, bunları için herhangi bir kod eklemeniz gerekmez.  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  Koleksiyon sınıfı ekleme `CreationEndpoint` CreationEndpointElement.cs dosyasında `CreationEndpoint` projesi. Bu sınıf tarafından yapılandırma bir dizi tutmak için kullanılan `CreationEndpoint` web.config dosyasında örnekleri.  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  Çözümü oluşturun.  
  
### <a name="host-the-workflow-in-iis"></a>IIS'de iş akışı barındırma  
  
1.  Adlı yeni bir uygulama oluşturmak `MyCreationEndpoint` IIS'de.  
  
2.  Uygulama dizini için iş akışı tasarımcısı tarafından oluşturulan workflow1.xaml dosyasını kopyalayın ve workflow1.xamlx için yeniden adlandırın.  
  
3.  Shared.dll ve CreationEndpoint.dll dosyalarını uygulamanın bin dizinine kopyalayın (bölme dizini mevcut değilse oluşturun).  
  
4.  Web.config dosyasında Değiştir `CreationEndpoint` proje ile aşağıdaki kodu.  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  Sonra `<system.web>` öğesi, kayıt `CreationEndpoint` aşağıdaki yapılandırma kodunu ekleyerek düzenleyin.  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     Bu kayıtları `CreationEndpointCollection` , yapılandırabilmek için sınıf bir `CreationEndpoint` web.config dosyasında.  
  
6.  Ekleme bir `<service>` öğesi (sonra \</extensions > etiketi) ile bir `CreationEndpoint` , gelen iletiler için dinleme.  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  Ekleme bir \<davranışları > öğesi (sonra  \< /Hizmetleri > etiketi) hizmeti meta verilerini sağlamak için.  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  Web.config, IIS uygulama dizinine kopyalayın.  
  
9. Oluşturma bitiş noktası tarafından Internet Explorer'ı başlatıp http://localhost/MyCreationEndpoint/Workflow1.xamlx için gözatma çalışıp çalışmadığını test edin. Internet Explorer, aşağıdaki ekran görüntülenmelidir:  
  
     ![Hizmet sınama](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a>CreationEndpoint çağıracak bir istemci oluşturun.  
  
1.  Yeni bir konsol uygulaması ekleyin `CreationEndpointTest` çözümü.  
  
2.  System.ServiceModel.dll, System.ServiceModel.Activities, başvurular ekleyin ve `Shared` projesi.  
  
3.  İçinde `Main` create yöntemi bir <xref:System.ServiceModel.ChannelFactory%601> türü `IWorkflowCreation` ve arama <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Bu proxy döndürür. Ardından çağırabilirsiniz `Create` iş akışı örneği oluşturmak için proxy üzerinde barındırılan IIS altında:  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  CreationEndpointClient çalıştırın. Çıktı aşağıdaki gibi görünmelidir:  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  Konsol çıktısı olan IIS altında çalıştığı için iş akışı çıktısı görmezsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek için tam kod aşağıda verilmiştir.  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 Hiçbir zaman uygulayan bir hizmet uyguladığınız için bu örnek karmaşık görünebilir `IWorkflowCreation`. Bunun nedeni, `CreationEndpoint` bunu sizin için yapar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Internet Information Services'te barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Internet Information Services barındırma en iyi uygulamaları](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Internet Information Service barındırma yönergeleri](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Windows iş akışı mimarisi](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [WorkflowHostingEndpoint Sürdür yer işareti](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [İş Akışı Tasarımcısı yeniden barındırma](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Windows iş akışı genel bakış](../../../../docs/framework/windows-workflow-foundation/overview.md)
