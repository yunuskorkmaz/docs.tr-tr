---
title: 'Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme'
description: Bir yapılandırma dosyasında bir WCF hizmeti için uç nokta yapılandırmayı öğrenin. Bir sözleşme, bir hizmet için tanımlanır ve bir sınıfa uygulanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 92d0834091a1f243df6be214f606fbf0093dca54
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244562"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="d191e-104">Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="d191e-104">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="d191e-105">Bu örnekte, bir `ICalculator` anlaşma temel Hesaplayıcı hizmeti için tanımlanmıştır, hizmet `CalculatorService` sınıfında uygulanır ve ardından uç noktası, hizmetin kullandığı Web.config dosyasında yapılandırılır <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="d191e-105">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="d191e-106">Bu hizmeti yapılandırma yerine kod kullanarak yapılandırma hakkında açıklama için bkz. [nasıl yapılır: kod Içinde hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="d191e-106">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="d191e-107">Genellikle, bağlama ve adres bilgilerini, kod içinde imperatively yerine bildirimli olarak yapılandırmaya göre belirlemek en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="d191e-107">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="d191e-108">Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="d191e-108">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="d191e-109">Daha genel olarak, bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d191e-109">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="d191e-110">Aşağıdaki yapılandırma adımlarının tümü, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d191e-110">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="d191e-111">Bu örneğin kaynak kopyası için bkz. [BasicBinding](./samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d191e-111">For the source copy of this example, see [BasicBinding](./samples/basicbinding.md).</span></span>  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="d191e-112">Hizmeti yapılandırmak için kullanılacak BasicHttpBinding 'i belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d191e-112">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1. <span data-ttu-id="d191e-113">Hizmet türü için bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d191e-113">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="d191e-114">Hizmet sözleşmesini bir hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d191e-114">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="d191e-115">Hizmet uygulamasının içinde adres veya bağlama bilgisi belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="d191e-115">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="d191e-116">Ayrıca, bu bilgileri yapılandırma dosyasından getirmek için kodun yazılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d191e-116">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3. <span data-ttu-id="d191e-117">Kullanan için bir uç nokta yapılandırmak üzere bir Web.config dosyası oluşturun `CalculatorService` <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="d191e-117">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
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
  
4. <span data-ttu-id="d191e-118">Aşağıdaki satırı içeren bir Service. svc dosyası oluşturun ve bunu Internet Information Services (IIS) sanal dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d191e-118">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="d191e-119">Bağlama özelliklerinin varsayılan değerlerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="d191e-119">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="d191e-120">Öğesinin varsayılan özellik değerlerinden birini değiştirmek için, <xref:System.ServiceModel.WSHttpBinding> öğesi içinde yeni bir bağlama yapılandırma adı oluşturun `<binding name="Binding1">` [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) ve bu Binding öğesindeki bağlamanın özniteliklerinin yeni değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d191e-120">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="d191e-121">Örneğin, varsayılan açık ve kapalı zaman aşımı değerlerini 1 dakikalık ila 2 dakikaya değiştirmek için yapılandırma dosyasına aşağıdakini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d191e-121">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d191e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d191e-122">See also</span></span>

- [<span data-ttu-id="d191e-123">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d191e-123">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d191e-124">Bir Uç Noktası Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="d191e-124">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
