---
title: 'Nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 1d9a6d0a556613576a14c600aa72d3f4524cdc3e
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029638"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="115b3-102">Nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme</span><span class="sxs-lookup"><span data-stu-id="115b3-102">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="115b3-103">Bu örnekte, bir `ICalculator` anlaşma temel hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıf ve onun uç noktası burada belirtilen hizmet kullandığını Web.config dosyasında yapılandırılmış <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="115b3-103">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="115b3-104">Yapılandırma yerine kod kullanarak bu hizmeti yapılandırmak nasıl bir açıklaması için bkz [nasıl yapılır: Kodda hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="115b3-104">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="115b3-105">Yapılandırma yerine kesin kod bağlama ve adres bilgilerini bildirimli olarak belirtmek için genellikle en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="115b3-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="115b3-106">Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="115b3-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="115b3-107">Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek için bunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="115b3-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="115b3-108">Tüm aşağıdaki yapılandırma adımlarını kullanarak gerçekleştirilen [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="115b3-108">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="115b3-109">Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="115b3-109">For the source copy of this example, see [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span></span>  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="115b3-110">BasicHttpBinding hizmeti yapılandırmak için kullanmak üzere belirtmek için</span><span class="sxs-lookup"><span data-stu-id="115b3-110">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1.  <span data-ttu-id="115b3-111">Hizmet türü için bir hizmet anlaşmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="115b3-111">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="115b3-112">Hizmet sözleşmesi bir hizmet sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="115b3-112">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="115b3-113">Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="115b3-113">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="115b3-114">Ayrıca, bu bilgileri yapılandırma dosyasından getirilecek yazılacak kod yok.</span><span class="sxs-lookup"><span data-stu-id="115b3-114">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3.  <span data-ttu-id="115b3-115">Bir uç nokta için yapılandırmak için bir Web.config dosyası oluşturma `CalculatorService` kullanan <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="115b3-115">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <!-- Leave the address blank to be populated by default -->  
            <!-- from the hosting environment,in this case IIS, so -->  
            <!-- the address will just be that of the IIS Virtual -->  
            <!-- Directory. -->  
                address=""   
            <!-- Specify the binding type -->  
                binding="wsHttpBinding"  
            <!-- Specify the binding configuration name for that -->  
            <!-- binding type. This is optional but useful if you -->  
            <!-- want to modify the properties of the binding. -->  
            <!-- The bindingConfiguration name Binding1 is defined -->  
            <!-- below in the bindings element. -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  <span data-ttu-id="115b3-116">Aşağıdaki satırı içeren bir Service.svc dosyası oluşturun ve, Internet Information Services (IIS) sanal dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="115b3-116">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="115b3-117">Bağlama özelliklerin varsayılan değerlerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="115b3-117">To modify the default values of the binding properties</span></span>  
  
1.  <span data-ttu-id="115b3-118">Varsayılan özellik değerlerini birini değiştirmek için <xref:System.ServiceModel.WSHttpBinding>, yeni bir bağlama Yapılandırması adı - oluşturma `<binding name="Binding1">` - içinde [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ve öznitelikleri için yeni değerleri ayarlayın Bu bağlama öğesi bağlama.</span><span class="sxs-lookup"><span data-stu-id="115b3-118">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="115b3-119">Örneğin, varsayılan açık değiştirmek ve 1 dakika ile 2 dakikalık zaman aşımı değerlerini kapatmak için yapılandırma dosyasına aşağıdakileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="115b3-119">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="115b3-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="115b3-120">See Also</span></span>  
 [<span data-ttu-id="115b3-121">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="115b3-121">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="115b3-122">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="115b3-122">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
